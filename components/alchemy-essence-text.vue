<template>
  <span>{{ content.ingredient }}</span>
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
