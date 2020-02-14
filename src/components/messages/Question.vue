<template lang="pug">
  .Question--content.d-flex.align-items-top.justify-content-left
    .question--thumbnail--container
      img#basileQuestionThumbnail(:src="basilePng")
    .question {{ title }}
</template>

<script>
import basilePng from '../../assets/bot.png'

export default {
  name: "Question",
  props: {
    title: String
  },
  data() {
    return {
      basilePng
    }
  }
}
</script>

<style lang="scss" scoped>
.Question--content {
  &.d-flex {
    width: 100%;
  }
  .question {
    &--thumbnail--container {
      max-width: 40px;
      overflow: hidden;
      margin: 4px;
      #basileQuestionThumbnail {
        max-width: 40px;
      }
    }
  }
}
</style>
