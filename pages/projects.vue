<template>
  <v-container>
    <v-row
      v-for="project in projects"
      :key="project.name"
      justify="center"
      class="ma-6"
    >
      <template>
        <v-hover v-slot="{ hover }">
          <v-card
            width="500"
            :href="project.url"
            elevation="20"
            :img="project.image"
            outlined
          >
            <v-card-title>{{ project.name }}</v-card-title>
            <v-card-text>{{ project.description }}</v-card-text>

            <v-card-title>
              <v-icon left class="mr-1">mdi-star-outline</v-icon>
              {{ project.stars }}
              <v-icon left class="mr-1 ml-2">mdi-source-fork</v-icon>
              {{ project.forks }}
            </v-card-title>
            <v-overlay v-if="hover" absolute></v-overlay>
          </v-card>
        </v-hover>
      </template>
    </v-row>
  </v-container>
</template>

<script>
export default {
  data() {
    return {
      repos: [
        {
          name: 'dNote',
          repo: 'dnote',
          image: '/background_5.jpg',
        },
        {
          name: 'KraK',
          repo: 'krak',
          image: '/background_2.jpg',
        },
        {
          name: 'KraK Server',
          repo: 'krak-server',
          image: '/background_3.jpg',
        },
        {
          name: 'This Website!',
          repo: 'yetisir.me',
          image: '/background_6.jpg',
        },
      ],
      projects: [],
    }
  },

  mounted() {
    this.repos.forEach((repo) => this.getGithubData(repo))
  },

  methods: {
    async getGithubData(repo) {
      const apiUrl = `https://api.github.com/repos/yetisir/${repo.repo}`

      const response = await this.$axios.$get(apiUrl)
      this.projects.push({
        url: response.html_url,
        description: response.description,
        stars: response.stargazers_count,
        watchers: response.watchers_count,
        forks: response.forks_count,
        name: repo.name,
        image: repo.image,
      })
    },
  },
}
</script>
