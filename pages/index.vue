<template lang="pug">
  div
    Content
      img#top-image(src="/page/images/top.png")
    Content#produced
      v-layout(justify-center)
        iframe(width="560" height="315" src="https://www.youtube.com/embed/KmXfQvU6zhU" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen)
    Content
      Profile
    Content
      v-container()
        v-content
          v-card(flat)
            v-toolbar(color="secondary" flat)
              v-toolbar-title
                v-icon(color="primary" medium) fab fa-github
                span  GitHub
            v-layout(row wrap)
              v-flex(md4 v-for="e in repos" :key="e.name")
                repository(v-bind:repository="e" v-bind:options="options")
</template>

<script>
import Vue from "vue"
import axios from "axios"
import Immutable from "immutable"
import moment from "moment"
import Content from "~/components/Content"
import Profile from "~/components/Profile"
import Repository from "~/components/Repository"

export default {
  data() {
    return {
      repos: [],
      options: {
        layout: {
          padding: {
            left: 0,
            right: 0,
            top: 0,
            bottom: 0
          }
        },
        legend: {
          display: true,
          position: "bottom"
        },
        maintainAspectRatio: true
      }
    }
  },
  components: {
    Content,
    Profile,
    Repository
  },
  mounted: async function() {
    this.repos = await this.getGitHubRepositories()
  },
  methods: {
    async getGitHubRepositories() {
      const res = await axios.get(
        "https://api.github.com/users/ktr03282/repos",
        {
          auth: { token: "8fa31bbddec4ee06c0674a85414076ec20145f2a" }
        }
      )

      const repositories = res.data.map(e => {
        return {
          name: e.name,
          html_url: e.html_url,
          description: e.description,
          languages_url: e.languages_url,
          updated_at: e.updated_at,
          owner: e.owner
        }
      })
      return repositories
    }
  }
}
</script>

<style lang="sass">
#top-image
  width: 100%

.fadeIn-enter-active, .fadeIn-leave-active
  transition: opacity 2s
.fadeIn-enter, .fadeIn-leave-to
  opacity: 0
</style>
