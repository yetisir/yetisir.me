<template>
  <v-app dark class="white">
    <app-bar />
    <navigation-bar>
      <navigation-bar-item
        v-for="(page, i) in pages"
        :key="i"
        :route="page.route"
        :icon="page.icon"
        :name="page.name"
      >
      </navigation-bar-item>
    </navigation-bar>
    <footer-bar />
    <v-main>
      <nuxt />
    </v-main>
  </v-app>
</template>

<script>
import NavigationBar from '@/components/NavigationBar'
import NavigationBarItem from '@/components/NavigationBarItem'
import AppBar from '@/components/AppBar'
import FooterBar from '@/components/FooterBar'

export default {
  components: {
    NavigationBar,
    NavigationBarItem,
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
          icon: 'mdi-school',
          name: 'Education',
          route: '/education',
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
      ],
    }
  },
}
</script>
