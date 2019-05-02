<template>
  <component
    :is="essenceComponent"
    v-if="content.ingredient"
    :content="content"
  />
</template>

<script>
import AlchemyEssenceRichtext from '~/components/alchemy-essence-richtext'
import AlchemyEssenceText from '~/components/alchemy-essence-text'
import AlchemyEssencePicture from '~/components/alchemy-essence-picture'

export default {
  components: {
    AlchemyEssenceRichtext,
    AlchemyEssenceText,
    AlchemyEssencePicture
  },
  props: {
    content: { type: Object, required: true }
  },
  data() {
    const essenceType = this.content.essenceType
    return {
      essenceComponent: essenceType.replace('::', '')
    }
  }
}
</script>
