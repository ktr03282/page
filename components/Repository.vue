<template lang="pug">
  div
    v-card(flat tile)
      v-card-title
        a(v-bind:href="repository.html_url")
          h3 {{ repository.name }}
      v-container(fluid)
        Doughnut.graph(v-if="Object.keys(languages).length > 1" v-bind:data="languages" v-bind:options="options")
      v-card-title
        span(style="font-size: 0.8em; opacity: 0.7") {{ repository.description }}
</template>

<script>
import Doughnut from "~/components/Doughnut"
import axios from "axios"
import colors from "~/assets/colors"

const createColors = (labels) => labels.map(e => colors[e])

export default {
  name: "repository",
  props:["repository", "options"],
  data () {
    return {
      languages: {}
    }
  },
  mounted: function () {
    axios.get(this.repository.languages_url)
      .then(langs => {
        const d = langs.data
        const labels = Object.keys(d)
        const sum = Object.values(d).map(e => parseInt(e, 10)).reduce((c, n) => c + n)
        const data = Object.values(d).map(e => Math.floor(e / sum * 10000) / 100)

        this.languages = {
          labels,
          datasets: [{
            backgroundColor: createColors(labels),
            data
          }]
        }
      })
  },
  components: {
    Doughnut
  }
}
</script>

<style scoped lang="sass">
.graph
  max-width: 200px
</style>
