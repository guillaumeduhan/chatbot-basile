<template lang="pug">
  .Answer--content.d-flex.align-items-end.justify-content-end
    .option.answer {{ title }}
</template>

<script>
export default {
  name: "Answer",
  props: {
    title: String
  },
}
</script>

<style lang="scss" scoped>
.Answer--content {
  &.d-flex {
    width: 100%;
    margin: 4px auto;
  }
}
</style>
