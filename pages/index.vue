<template lang="pug">
  div
    Content#produced
      v-container()
        v-content
          div(style="text-align: center")
            h1 For What?
            p GitHubリポジトリや過去に自分が作成したもの、今後やりたいことなど色々まとめていきます。
          v-layout(justify-center)
            iframe(width="560" height="315" src="https://www.youtube.com/embed/KmXfQvU6zhU" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen)
    Content
      div(style="position:relative;width:100%;height:0;padding-bottom:calc(56.25% + 40px);")
        iframe(allowfullscreen style="position:absolute; width: 100%; height: 100%;border: solid 1px #333;" src="https://www.beautiful.ai/player/-LEoCQaYJkxoQm03Sreo/profile")
      Profile
    Content
      v-container()
        v-content
          v-card(flat)
            v-toolbar(color="white" flat)
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
  mounted: function() {
    this.setRepositories("https://api.github.com/users/ktr03282/repos")
  },
  methods: {
    async getGitHubRepositories(url) {
      const res = await axios.get(
        url,
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
    },
    async setRepositories(url) {
      this.repos = await this.getGitHubRepositories(url)
    }
  }
}
</script>

<style lang="sass">
.fadeIn-enter-active, .fadeIn-leave-active
  transition: opacity 2s
.fadeIn-enter, .fadeIn-leave-to
  opacity: 0
</style>
