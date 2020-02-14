<template lang="pug">
  .Timeline.d-flex.flex-column.justify-content-end.align-items-center
    .Timeline--content
      .Timeline--model(v-for="(line, index) in conversation", :key="index")
        Question(v-if="line.type === 'question'", :title="line.title")
        Answer(v-if="line.type === 'answer'", :title="line.title")
    TypingLoader(v-if="loading")
    .Timeline--options.d-flex.align-items-center.justify-content-center
      Button(v-if="answers.length", v-for="(answer, index) in answers", :key="index", :title="answer.title", classType="option", @click.native="pushAnswer(answer)")
</template>

<script>
import Answer from './messages/Answer.vue'
import Button from './Button.vue'
import Question from './messages/Question.vue'
import TestSide from './TestSide.vue'
import TypingLoader from './TypingLoader.vue'

import dataJson from '../../data.json'

export default {
  name: "Timeline",
  components: {
    Answer,
    Button,
    Question,
    TestSide,
    TypingLoader
  },
  data() {
    return {
      answers: [],
      dataJson,
      conversation: [],
      loading: false
    }
  },
  methods: {
    initConversation() {
      this.findQuestion("1")
    },
    findQuestion (number) {
      _.forEach(dataJson.data, (question, key) => {
        if (key === number) {
          this.pushQuestion(question)
        }
      })
    },
    pushAnswer(answer) {
      this.conversation.push(answer)
      this.answers = []
      this.findQuestion(answer.linkTo)
    },
    pushQuestion(question) {
      this.loading = true
      if (question.delay) {
        setTimeout(()=> {
          this.conversation.push(question)
          _.forEach(question.answers, (answer) => {
            this.answers.push(answer)
          })
          if (question.next) {
            this.findQuestion(question.next)
          } else {
            this.loading = false
          }
        }, question.delay)
      }
    }
  },
  mounted() {
    this.initConversation()
  }
}
</script>

<style lang="scss" scoped>
.Timeline {
  width: 100vw;
  height: 100vh;
  padding: 25px;

  &--content {
    width: 100%;
  }
}
</style>
