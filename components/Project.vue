<template>
  <card
    :title="name"
    :url="url"
    :url-icon="urlIcon"
    :image="image"
    :loading="loading"
    :bodyMd="readme"
    :subtitle="description"
  >
    <v-card-title>
      <v-icon left class="mr-1">mdi-star-outline</v-icon>
      {{ stars }}
      <v-icon left class="mr-1 ml-2">mdi-source-fork</v-icon>
      {{ forks }}
    </v-card-title>
  </card>
</template>

<script>
import Card from '@/components/Card'

export default {
  components: {
    Card,
  },
  props: {
    image: {
      type: String,
      default: '',
    },
    name: {
      type: String,
      default: '',
    },
    repo: {
      type: String,
      default: '',
    },
  },

  data() {
    return {
      mouseOver: false,
      url: '',
      urlIcon: 'mdi-github',
      description: '',
      stars: null,
      watchers: null,
      forks: null,
      loading: true,
      readme: '',
    }
  },

  mounted() {
    this.getGithubData()
  },

  methods: {
    async getGithubData() {
      const apiUrl = `https://api.github.com/repos/${this.repo}`

      const response = await this.$axios.$get(apiUrl)
      this.url = response.html_url
      this.description = response.description
      this.stars = response.stargazers_count
      this.watchers = response.watchers_count
      this.forks = response.forks_count

      const readmeResponse = await this.$axios.$get(`${apiUrl}/readme`)

      const readme = atob(readmeResponse.content)

      this.readme = readme.substring(readme.indexOf('#') - 1)
      this.loading = false
    },
  },
}
</script>
