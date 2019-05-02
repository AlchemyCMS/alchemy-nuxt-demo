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
      required: true
    }
  },
  data() {
    return {
      page: {}
    }
  },
  apollo: {
    page: {
      query: gql`
        query PageByName($name: String) {
          page: alchemyPage(name: $name) {
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
      `,
      variables() {
        return {
          name: this.pageName
        }
      }
    }
  }
}
</script>
