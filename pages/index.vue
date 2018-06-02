<template lang="pug">
  section
    Profile
    v-container()
      h2 GitHub
      v-content
        v-card
          v-layout(row wrap)
            v-flex(md4 v-for="e in repos" :key="e.name")
              repository(v-bind:repository="e" v-bind:options="options")
</template>

<script>
import Vue from "vue"
import axios from "axios"
import Immutable from "immutable"
import moment from "moment"
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
    Profile,
    Repository
  },
  mounted: async function() {
    this.repos = await this.getGitHubRepositories()
  },
  methods: {
    async getGitHubRepositories() {
      const res = await axios.get(
        "https://api.github.com/users/ktr03282/repos"
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

<style>
</style>
