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
          tech: [
            'Search Engine Indexing',
            'Natural Language Processing',
            'CLI',
            'Python',
            'PyTest',
            'AWS DynamoDB',
            'TravisCI',
            'MkDocs',
            'PyPi Deployment',
            'Read the Docs',
          ],
        },
        {
          name: 'KraK',
          repo: 'yetisir/krak',
          tech: [
            'Python',
            '3d Geometry Processing',
            'Visualization Toolkit (VTK)',
            'Computational Mechanics',
            'Scientific Simulation',
            'CircleCI',
            'PyPi',
            'Mesh Generation',
            'Docker',
          ],
        },
        {
          name: 'KraK Server',
          repo: 'yetisir/krak-server',
          tech: [
            'Javascript',
            'Python',
            'Vue.js',
            'Vuex',
            'VTK.js',
            'Twisted',
            'Websockets',
            'RESTful API',
            'Docker',
            'WSLink',
            'Paraview',
            'Server Side Rendering',
            'nginx',
            'PostgreSQL',
            'Sandbox',
            'AWS EC2',
          ],
        },
        {
          name: 'This Website',
          repo: 'yetisir/yetisir.me',
          tech: [
            'Vue.js',
            'Nuxt',
            'Static Hosting',
            'AWS S3',
            'Github Actions CI',
            'Javascript',
          ],
        },
        {
          name: 'Resume',
          repo: 'yetisir/resume',
          tech: ['LaTeX', 'BibTeX', 'Makefile', 'Docker', 'docker-compose'],
        },
        {
          name: 'Krak API',
          repo: 'yetisir/krak-openapi',
          tech: ['OpenAPI'],
        },
        {
          name: 'MOUSE',
          repo: 'yetisir/MOUSE',
          tech: ['Python'],
        },
        {
          name: 'Masters Thesis',
          repo: 'yetisir/masters-thesis',
          tech: ['LaTeX'],
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
