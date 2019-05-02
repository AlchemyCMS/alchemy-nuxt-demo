<template>
  <section>
    <h1>{{ page.name }}</h1>
    <alchemy-element
      v-for="element in page.elements"
      :key="element.id"
      :element="element"
    />
  </section>
</template>

<script>
import gql from 'graphql-tag'
import AlchemyElement from '~/components/alchemy-element'

export default {
  components: {
    AlchemyElement
  },
  props: {
    pageName: {
      type: String,
      default: null
    },
    pageUrl: {
      type: String,
      default: null
    },
    pageType: {
      type: String,
      default: null
    }
  },
  data() {
    return {
      page: {}
    }
  },
  apollo: {
    page: {
      query() {
        let variable = 'name'
        let argument = 'name'

        if (this.pageUrl) {
          variable = 'url'
          argument = 'urlname'
        } else if (this.pageType) {
          variable = 'type'
          argument = 'pageLayout'
        }

        return gql`
          query Page($${variable}: String) {
            page: alchemyPage(${argument}: $${variable}) {
              name
              elements {
                id
                contents {
                  id
                  name
                  essenceType
                  ingredient
                }
              }
            }
          }
        `
      },
      variables() {
        return {
          name: this.pageName,
          url: this.pageUrl,
          type: this.pageType
        }
      }
    }
  }
}
</script>
