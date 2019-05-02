<template>
  <section class="container">
    <alchemy-page :page-url="pageUrl" />
  </section>
</template>

<script>
import AlchemyPage from '~/components/alchemy-page'

export default {
  components: {
    AlchemyPage
  },
  computed: {
    pageUrl() {
      return `products/${this.$route.params.slug}`
    }
  }
}
</script>
