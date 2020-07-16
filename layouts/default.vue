<template>
  <v-app dark class="white">
    <!-- <v-app-bar app src="/background.jpg"> -->
    <v-app-bar app hide-on-scroll border outline flat class="transparent">
      <v-divider></v-divider>
      <v-card shaped>
        <v-card-title class="title">
          M. Yetisir
        </v-card-title>
      </v-card>
    </v-app-bar>
    <navigation-bar :pages="pages" />

    <v-main>
      <nuxt />
    </v-main>

    <v-footer app>
      <span>&copy; M. Yetisir {{ new Date().getFullYear() }}</span>
    </v-footer>
  </v-app>
</template>

<script>
import NavigationBar from '@/components/NavigationBar'
export default {
  components: {
    NavigationBar,
  },
  props: {
    navigationDrawerBackgroundSource: {
      type: String,
      default: '/background_2.jpg',
    },
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
          icon: 'mdi-chart-bubble',
          name: 'Projects',
          route: '/projects',
        },
        {
          icon: 'mdi-newspaper',
          name: 'Publications',
          route: '/publications',
        },
        {
          icon: 'mdi-contacts',
          name: 'Contact',
          route: '/contact',
        },
        {
          icon: 'mdi-smoke-detector',
          name: 'Smoke',
          route: '/smoke',
        },
      ],
    }
  },
  computed: {
    navigationDrawerBackground() {
      return this.navigationDrawerOpen
        ? null
        : this.navigationDrawerBackgroundSource
    },
  },
  methods: {
    getNavigationHoverStatus(test) {
      const hovering = this.pages.filter((page) => {
        return page.hover
      })
      return hovering.length >= 1
    },
    setHoverStatus(pageIndex, val) {
      this.pages[pageIndex].hover = val
    },
  },
}
</script>
<style>
.theme--dark.v-application {
  background-color: var(--v-background-base, black) !important;
}
.theme--light.v-application {
  background-color: var(--v-background-base, white) !important;
}

.title {
  text-align: center;
  text-justify: center;
  font-size: 25em;
  color: #fff;
  letter-spacing: -7px;
  font-weight: 700;
  text-transform: uppercase;
  animation: blur 0.5s ease-out infinite alternate-reverse;
  text-shadow: 0 0 5px #fff, 0 0 7px #fff;
}

@keyframes blur {
  from {
    text-shadow: 0 0 10px #fff, 0 0 15px #fff;
  }
}
</style>
