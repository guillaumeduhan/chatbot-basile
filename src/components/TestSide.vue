<template lang="pug">
#TestSide
  header
    img#logo(:src="botLogo")
  .question Ceci est une question ?
  Button(title="Ceci est une option", classType="option")
  Button(title="Ceci est une réponse", classType="option answer")
  .description Ceci est une description
  Button(title="Ceci est un bouton action", classType="action")
  Button(classType="link", :linkContent="exampleLink")
</template>

<script>
import Button from './Button.vue'
import testImg from '../assets/test.jpg'
import botLogo from '../assets/bot.png'

export default {
  name: 'TestSide',
  components: {
    Button,
  },
  data(){
    return {
      botLogo,
      exampleLink: {
        description: 'Ceci est une description test',
        imgSrc: testImg,
        link: 'https://myhappyagency.com',
        title: 'Ceci est un titre test'
      }
    }
  }
}
</script>

<style lang="scss" scoped>
</style>
