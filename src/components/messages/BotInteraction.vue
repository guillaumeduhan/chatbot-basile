<template lang="pug">
  .BotInteraction--content.d-flex.align-items-top.justify-content-left
    .question--thumbnail--container
      img#basileQuestionThumbnail(:src="basilePng")
    .question(v-if="content.type === 'questionTitle'") {{ content.title }}
    .answer(v-if="content.type === 'answerLink'")
      Button(classType="link", :linkContent="content")
</template>

<script>
import Button from '../Button.vue'
import basilePng from '../../assets/bot.png'

export default {
  name: "BotInteraction",
  props: {
    content: Object,
    title: String,
    type: String
  },
  data() {
    return {
      basilePng
    }
  },
  components: {
    Button
  }
}
</script>

<style lang="scss" scoped>
.BotInteraction--content {
  &.d-flex {
    width: 100%;
  }
  .question {
    &--thumbnail--container {
      min-width: 40px;
      max-height: 40px;
      overflow: hidden;
      margin: 4px;
      border-radius: 50px;
      #basileQuestionThumbnail {
        max-width: 40px;
      }
    }
  }
}
</style>
