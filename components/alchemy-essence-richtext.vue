<template>
  <!-- eslint-disable-next-line -->
  <div v-html="content.ingredient" />
</template>

<script>
export default {
  props: {
    content: {
      type: Object,
      required: true
    }
  }
}
</script>
