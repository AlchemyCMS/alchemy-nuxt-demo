<template>
  <img :src="content.ingredient" />
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
