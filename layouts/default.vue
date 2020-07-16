<template>
  <v-app dark class="white">
    <app-bar />
    <navigation-bar :pages="pages" />
    <footer-bar />
    <v-main>
      <nuxt />
    </v-main>
  </v-app>
</template>

<script>
import NavigationBar from '@/components/NavigationBar'
import AppBar from '@/components/AppBar'
import FooterBar from '@/components/FooterBar'

export default {
  components: {
    NavigationBar,
    AppBar,
    FooterBar,
  },
  data() {
    return {
      pages: [
        {
          icon: 'mdi-home',
          name: 'Home',
          route: '/',
        },
        {
          icon: 'mdi-rocket-launch',
          name: 'Work Experience',
          route: '/experience',
        },
        {
          icon: 'mdi-chart-bubble',
          name: 'Open Source Projects',
          route: '/projects',
        },
        {
          icon: 'mdi-newspaper',
          name: 'Publications and Conferences',
          route: '/publications',
        },
        {
          icon: 'mdi-contacts',
          name: 'Contact',
          route: '/contact',
        },
        {
          icon: 'mdi-smoke-detector',
          name: 'Test Page',
          route: '/test',
        },
      ],
    }
  },
}
</script>
