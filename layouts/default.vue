<template lang="pug">
  v-app
    img#top-image(src="https://user-images.githubusercontent.com/39692091/41200768-2185ac42-6ce6-11e8-8ebb-2ee243deeb13.png")
    v-content
      nuxt
</template>

<script>
export default {
  data () {
    return {
    }
  }
}
</script>

<style>
html {
  font-family: "Source Sans Pro", -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif;
  font-size: 16px;
  word-spacing: 1px;
  -ms-text-size-adjust: 100%;
  -webkit-text-size-adjust: 100%;
  -moz-osx-font-smoothing: grayscale;
  -webkit-font-smoothing: antialiased;
  box-sizing: border-box;
}

*, *:before, *:after {
  box-sizing: border-box;
  margin: 0;
}

#top-image {
  width: 100%;
}
</style>
