<template lang="pug">
  #Loader.d-flex.flex-column.align-items-center.justify-content-center
    .loader-container
      .loader-bar
    img#botLoaderImage(:src="botpng")
    .description Basile est un assistant intelligent qui répondra à toutes vos questions concernant la création d'entreprise.
</template>

<script>
import botpng from '../assets/bot.png'

export default {
  name: "Loader",
  data() {
    return {
      botpng
    }
  }
}
</script>

<style lang="scss" scoped>
#Loader {
  width: 100vw;
  height: 100vh;
  position: relative;

  #botLoaderImage {
    max-width: 75px;
    animation-name: jump;
    animation-timing-function: ease;
  }

  .loader-container {
    width: 100%;
    height: 10px;
    position: absolute;
    top: 0px;

    .loader-bar {
      height: 10px;
      background: $ocean;
      -webkit-animation: loading 4s forwards; /* Safari 4+ */
      -moz-animation:    loading 4s forwards; /* Fx 5+ */
      -o-animation:      loading 4s forwards; /* Opera 12+ */
      animation:         loading 4s forwards; /* IE 10+, Fx 29+ */
    }
  }
}

@keyframes jump {
    0%   { transform: scale(1,1)    translateY(0); }
    10%  { transform: scale(1.1,.9) translateY(0); }
    30%  { transform: scale(.9,1.1) translateY(-100px); }
    50%  { transform: scale(1,1)    translateY(0); }
    57%  { transform: scale(1,1)    translateY(-7px); }
    64%  { transform: scale(1,1)    translateY(0); }
    100% { transform: scale(1,1)    translateY(0); }
}

@keyframes loading {
  0% {
    width: 0%;
  }
  25% {
    width: 23%;
  }
  50% {
    width: 36%;
  }
  80% {
    width: 76%;
    height: 10px;
  }
  100% {
    width: 100%;
  }
}
</style>
