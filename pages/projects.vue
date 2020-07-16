<template>
  <v-container>
    <v-row v-for="repo in repos" :key="repo.name" justify="center" class="ma-6">
      <project :name="repo.name" :repo="repo.repo" :image="repo.image" />
    </v-row>
  </v-container>
</template>

<script>
import Project from '@/components/Project'

export default {
  components: {
    Project,
  },
  data() {
    return {
      repos: [
        {
          name: 'dNote',
          repo: 'yetisir/dnote',
          image: '/background_5.jpg',
        },
        {
          name: 'KraK',
          repo: 'yetisir/krak',
          image: '/background_2.jpg',
        },
        {
          name: 'KraK Server',
          repo: 'yetisir/krak-server',
          image: '/background_3.jpg',
        },
        {
          name: 'This Website',
          repo: 'yetisir/yetisir.me',
          image: '/background_6.jpg',
        },
      ],
    }
  },
}
</script>
