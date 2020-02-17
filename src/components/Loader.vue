<template lang="pug">
  #Loader(:class="{ 'disappear' : isMoving }")
    .loader-container-full.d-flex.flex-column.align-items-center.justify-content-center
      .loader-container-image
        img#botLoaderImage(:src="botpng")
      .loader-infos
        .description.loader-description-appear Basile est un assistant intelligent qui répondra à toutes vos questions concernant la création d'entreprise.
        .loader-container
          .loader-bar
</template>

<script>
import botpng from '../assets/bot.png'

export default {
  name: "Loader",
  data() {
    return {
      botpng,
      isMoving: false
    }
  },
  mounted() {
    setTimeout(() => {
      this.isMoving = true
    }, 10000)
  }
}
</script>

<style lang="scss" scoped>
#Loader {
  width: 100vw;
  height: 100vh;
  position: absolute;
  top: 0;
  left: 0;
  z-index: 10000;
  background: white;
  overflow: hidden;

  &.disappear {
    -webkit-animation: disappear 2s forwards; /* Safari 4+ */
    -moz-animation:    disappear 2s forwards; /* Fx 5+ */
    -o-animation:      disappear 2s forwards; /* Opera 12+ */
    animation:         disappear 2s forwards; /* IE 10+, Fx 29+ */
  }

  .loader-container-full{
    width: 100vw;
    height: 100vh;
    position: relative;

    .loader-container-image{
      width: 100%;
      height: 75px;
      position: relative;
      margin-bottom: 25px;
      border-radius: 50px;
      overflow: hidden;

      #botLoaderImage {
        max-width: 75px;
      }
    }

    &.remove {
      display: none!important;
    }

    .loader-infos {
      max-width: 600px;
      -webkit-animation: reduce 7s forwards; /* Safari 4+ */
      -moz-animation:    reduce 7s forwards; /* Fx 5+ */
      -o-animation:      reduce 7s forwards; /* Opera 12+ */
      animation:         reduce 7s forwards; /* IE 10+, Fx 29+ */
      overflow: hidden;
      height: 100px;

      .loader-description-appear {
        margin: 25px auto;
        -webkit-animation: appear 2s forwards; /* Safari 4+ */
        -moz-animation:    appear 2s forwards; /* Fx 5+ */
        -o-animation:      appear 2s forwards; /* Opera 12+ */
        animation:         appear 2s forwards; /* IE 10+, Fx 29+ */
      }

      .loader-container {
        height: 10px;
        margin: 25px auto;
        max-width: 200px;

        .loader-bar {
          height: 2px;
          border-radius:50px;
          background: $gradient;
          -webkit-animation: loading 4s forwards; /* Safari 4+ */
          -moz-animation:    loading 4s forwards; /* Fx 5+ */
          -o-animation:      loading 4s forwards; /* Opera 12+ */
          animation:         loading 4s forwards; /* IE 10+, Fx 29+ */
        }
      }
    }
  }
}

@keyframes appear {
    0%   {
      opacity: 0;
    }
    100% {
      opacity: 1;
      margin: 0;
    }
}

@keyframes disappear {
    0%   {
      opacity: 1;
    }
    100% {
      opacity: 0;
    }
}

@keyframes reduce {
    0%   {
      height: 100px;
    }
    80% {
      height: 100px;
    }
    100% {
      height: 0px;
      display: none;
    }
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
  }
  100% {
    width: 100%;
  }
}
</style>
