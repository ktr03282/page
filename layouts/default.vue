<template lang="pug">
  v-app
    v-toolbar(app color="primary" dark)
      v-toolbar-side-icon.hidden-sm-and-up(@click.stop="navBar = !navBar")
      v-toolbar-title Portfolio
      v-spacer
      v-toolbar-items.hidden-sm-and-down
        v-btn(flat) hoge
        v-btn(flat) hoge
        v-btn(flat) hoge
    v-navigation-drawer.hidden-sm-and-up(app v-model="navBar")
      v-toolbar(flat color="secondary")
        v-list
          v-list-tile
            v-list-tile-title a
      v-list
        v-list-tile
          h3 hoge
        v-list-tile
          h3 hoge
        v-list-tile
          h3 hoge
    v-content
      v-container(fluid)
        nuxt
</template>

<script>
export default {
  data () {
    return {
      navBar: false
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

</style>
