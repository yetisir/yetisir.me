<template>
  <v-hover v-slot="{ hover }">
    <v-card
      width="500"
      :href="url"
      target="_blank"
      elevation="20"
      :img="image"
      outlined
    >
      <v-card-title>{{ name }}</v-card-title>
      <v-card-text>
        <v-progress-circular
          v-if="!description"
          color="primary"
          indeterminate
        ></v-progress-circular>
        {{ description }}
      </v-card-text>

      <v-card-title>
        <v-icon left class="mr-1">mdi-star-outline</v-icon>
        {{ stars }}
        <v-icon left class="mr-1 ml-2">mdi-source-fork</v-icon>
        {{ forks }}
      </v-card-title>
      <v-overlay v-if="hover" absolute></v-overlay>
    </v-card>
  </v-hover>
</template>

<script>
export default {
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
      loaded: false,
      hover: false,
      url: null,
      description: null,
      stars: null,
      watchers: null,
      forks: null,
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
    },
  },
}
</script>
