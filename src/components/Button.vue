<template lang="pug">
  .button(:class="classType")
    .link-content-container(v-if="linkContent", @click="openUrl")
      .link-image(:style="{ backgroundImage: `url(${linkContent.imgSrc})` }")
      .link-content.d-flex.align-items-end.justify-content-between
        .link-text
          .link-title {{ linkContent.title }}
          .link-description {{ linkContent.description }}
        .link-image-link
          img(:src="linkImg")
    p(v-else, :class="{ 'lowerFont' : $mq === 'mobile' }") {{ title }}
</template>

<script>
import linkImg from '../assets/link.png'

export default {
  name: "Button",
  props: {
    classType: String,
    linkContent: Object,
    title: String
  },
  data() {
    return {
      linkImg
    }
  },
  methods: {
    openUrl() {
      if (this.linkContent.toUrl) {
        window.open(this.linkContent.toUrl, '_blank')
      }
    }
  }
}
</script>

<style lang="scss" scoped>
  .button {
    font-size: 18px;
    border: 1px solid transparent;
    width: fit-content;
    margin: 4px;

    &.action {
      background: $paradise;
      color: white;
      cursor: pointer;
      font-weight: 600;
      border-radius: 50px;
      padding: 9px 24px;

      &:hover {
        background: $ocean;
        transition: .25s;
        color: white;
      }
    }

    &.link {
      cursor: pointer;
      .link-content-container {
        min-width: 300px;
        max-width: 100%;
        min-height: 250px;
        border-radius: 25px;
        overflow: hidden;
        background: black;
        position: relative;
        transition: .25s;

        .link-image {
          max-width: 400px;
          min-height: 250px;
          background-size: cover;
          background-position: center center;
          opacity: .70;
        }

        .link-content {
          position: absolute;
          bottom: 0;
          padding: 20px;
          min-width: 300px;
          max-width: 100%;
          max-height: 150px;
          text-align: left;

          .link-image-link {
            min-width: 30px;
            img {
              width: 25px;
            }
            overflow: hidden;
          }
          .link-title {
            font-size: 24px;
            line-height: 1.2;
            color: white;
            font-weight: 900;
          }
          .link-description {
            color: white;
            line-height: 1.2;
          }
        }
      }
    }

    p {
      margin: 0;

      &.lowerFont {
        font-size: 15px;
      }
    }
  }
</style>
