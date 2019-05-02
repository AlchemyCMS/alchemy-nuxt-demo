<template>
  <section>
    <alchemy-content
      v-for="content in element.contents"
      :key="content.id"
      :content="content"
    />
  </section>
</template>

<script>
import AlchemyContent from '~/components/alchemy-content.vue'

export default {
  components: {
    AlchemyContent
  },
  props: {
    element: {
      type: Object,
      required: true
    }
  }
}
</script>
