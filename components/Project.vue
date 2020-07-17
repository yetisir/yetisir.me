<template>
  <!-- <vue-glow color="white" :elevation="mouseOver ? 10 : 0"> -->
  <v-card
    width="500"
    :href="url"
    target="_blank"
    elevation="20"
    :img="image"
    outlined
    :loading="loading"
    @mouseenter="mouseOver = true"
    @mouseleave="mouseOver = false"
  >
    <v-card-title :class="[mouseOver ? 'glow' : '']">{{ name }}</v-card-title>
    <v-card-text>
      {{ description }}
    </v-card-text>

    <v-card-title>
      <v-icon left class="mr-1">mdi-star-outline</v-icon>
      {{ stars }}
      <v-icon left class="mr-1 ml-2">mdi-source-fork</v-icon>
      {{ forks }}
    </v-card-title>
    <v-overlay v-if="mouseOver" absolute></v-overlay>
  </v-card>
  <!-- </vue-glow> -->
</template>

<script>
// import VueGlow from 'vue-glow'

export default {
  // components: {
  //   VueGlow,
  // },
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
      url: null,
      description: null,
      stars: null,
      watchers: null,
      forks: null,
      loading: true,
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

      this.loading = false
    },
  },
}
</script>
