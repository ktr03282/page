<template lang="pug">
  section
    h1.header Portfolio
    h2 test
    v-btn(color="primary") button
    v-btn(color="secondary") button
    v-btn(color="accent") button
    v-btn(color="error") button
</template>

<script>
import axios from "axios"

export default {
  components: {
  },
  mounted: async function() {
    const repos = await this.getGitHubRepositories()
    console.log(repos)
  },
  methods: {
    getGitHubRepositories() {
      return new Promise((resolve, reject) => {
        axios.get("https://api.github.com/users/ktr03282/repos")
          .then(res => {
            const repositories = res.data.map(e => {
              return {
                name: e.name,
                html_url: e.html_url,
                languages_url: e.languages_url,
                updated_at: e.updated_at,
                owner: e.owner
              }
            })
            resolve(repositories)
          })
          .catch(err => reject(err))
      })
    }
  }
}
</script>

<style>
</style>
