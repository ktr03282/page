<template lang="pug">
  div.wrapper()
    slot.content()
</template>

<script>
export default {
  name: "contents",
  data () {
    return {
      height: 0
    }
  },
  mounted: function() {
    this.setWindowHeight()
  },
  methods: {
    setWindowHeight: function() {
      this.height = window.innerHeight
    }
  }
}
</script>

<style lang="sass" scoped>
.wrapper
  padding-top: 100px
  padding-bottom: 100px
  // text-align: center
  .content
</style>
