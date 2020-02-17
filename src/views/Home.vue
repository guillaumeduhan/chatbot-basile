<template lang="pug">
#Home
  Loader(v-if="showLoader")
  Timeline
</template>

<script>
import Loader from '../components/Loader.vue'
import TestSide from '../components/TestSide.vue'
import Timeline from '../components/Timeline.vue'
import botpng from '../assets/bot.png'

export default {
  name: 'Home',
  components: {
    Loader,
    Timeline,
    TestSide
  },
  data() {
    return {
      botpng,
      showLoader: false
    }
  },
  mounted() {
    setTimeout(() => {
      this.showLoader = false
    }, 10000)
  }
}
</script>

<style lang="scss">
#Home {
  img {
    max-width: 400px;
  }
  #logo {
    max-width: 75px;
    margin-bottom: 25px;
  }
}
</style>
