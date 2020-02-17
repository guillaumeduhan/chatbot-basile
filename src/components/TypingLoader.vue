 <template lang="pug">
  #TypingLoader.d-flex.align-items-top.justify-content-left
    .question--thumbnail--container
      img#basileQuestionThumbnail(:src="basilePng")
    .question.d-flex.align-items-center.justify-content-left
      span
      span
      span
</template>

<script>
import basilePng from '../assets/bot.png'

export default {
  name: "TypingLoader",
  data() {
    return {
      basilePng
    }
  }
}
</script>

<style lang="scss" scoped>
#TypingLoader {
  &.d-flex {
    width: 100%;
  }

  .question {
    -webkit-animation: grow 1.5s infinite; /* Safari 4+ */
    -moz-animation:    grow 1.5s infinite; /* Fx 5+ */
    -o-animation:      grow 1.5s infinite; /* Opera 12+ */
    animation:         grow 1.5s infinite; /* IE 10+, Fx 29+ */
    &--thumbnail--container {
      max-width: 40px;
      overflow: hidden;
      margin: 4px;
      border-radius: 40px;
      #basileQuestionThumbnail {
        max-width: 40px;
      }
    }

    span {
      background: $fish;
      opacity: 0.25;
      width: 10px;
      height: 10px;
      border-radius: 10px;
      display: block;
      &:first-child {
        margin-right: 2px;
        -webkit-animation: jump 1.5s infinite; /* Safari 4+ */
        -moz-animation:    jump 1.5s infinite; /* Fx 5+ */
        -o-animation:      jump 1.5s infinite; /* Opera 12+ */
        animation:         jump 1.5s infinite; /* IE 10+, Fx 29+ */
      }
      &:nth-child(2) {
        -webkit-animation: jump 1.5s infinite; /* Safari 4+ */
        -moz-animation:    jump 1.5s infinite; /* Fx 5+ */
        -o-animation:      jump 1.5s infinite; /* Opera 12+ */
        animation:         jump 1.5s infinite; /* IE 10+, Fx 29+ */
        animation-delay: .15s;
      }
      &:last-child {
        margin-left: 2px;
        -webkit-animation: jump 1.5s infinite; /* Safari 4+ */
        -moz-animation:    jump 1.5s infinite; /* Fx 5+ */
        -o-animation:      jump 1.5s infinite; /* Opera 12+ */
        animation:         jump 1.5s infinite; /* IE 10+, Fx 29+ */
        animation-delay: .30s;
      }
    }
  }
}

@-webkit-keyframes grow {
    0% {
        -webkit-transform:scale(0.9);
    }
    50% {
        -webkit-transform:scale(1);
    }
    100% {
        -webkit-transform:scale(0.9);
    }
}

@keyframes jump {
    0%   {
      transform: translateY(0);
    }
    50%  {
      transform: translateY(-5px);
      opacity: .75;
    }
    100% {
      transform: translateY(0);
    }
}
</style>
