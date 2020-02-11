<template lang="pug">
#Home
  Loader
</template>

<script>
import Loader from '../components/Loader.vue'

export default {
  name: 'Home',
  components: {
    Loader
  },
}
</script>

<style lang="scss">
#Home {
  img {
    max-width: 400px;
  }
}
</style>
