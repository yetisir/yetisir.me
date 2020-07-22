<template>
  <v-container>
    <h1 class="h1">{{ title }}</h1>
    <v-row
      v-for="(repo, index) in repos"
      :key="index"
      justify="center"
      class="ma-6"
    >
      <project
        :name="repo.name"
        :repo="repo.repo"
        :image="repo.image"
        :tech="repo.tech"
      />
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
      title: 'Open Source Projects',
      repos: [
        {
          name: 'dNote',
          repo: 'yetisir/dnote',
          // image: '/background_5.jpg',
          tech: [
            'Bash',
            'Search Engine Indexing',
            'Natural Language Processing',
            'CLI',
            'Python',
            'AWS DynamoDB',
            'TravisCI',
            'MkDocs',
            'Dependabot',
            'PyPi Deployment',
            'Read the Docs',
          ],
        },
        {
          name: 'KraK',
          repo: 'yetisir/krak',
          // image: '/background_2.jpg',
          tech: [
            'Python',
            '3d Geometry Processing',
            'Visualization Toolkit (VTK)',
            'Computational Mechanics',
            'Scientific Simulation',
            'CircleCI',
            'PyPi',
            'Mesh Generation',
          ],
        },
        {
          name: 'KraK Server',
          repo: 'yetisir/krak-server',
          // image: '/background_3.jpg',
        },
        {
          name: 'This Website',
          repo: 'yetisir/yetisir.me',
          // image: '/background_6.jpg',
        },
        {
          name: 'Resume',
          repo: 'yetisir/resume',
          // image: '/background_4.jpg',
        },
        {
          name: 'MOUSE',
          repo: 'yetisir/MOUSE',
          // image: '/background_5.jpg',
        },
        {
          name: 'Masters Thesis',
          repo: 'yetisir/masters-thesis',
          // image: '/background_2.jpg',
        },
      ],
    }
  },
  head() {
    return {
      title: this.title,
    }
  },
}
</script>
