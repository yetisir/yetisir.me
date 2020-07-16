<template>
  <v-app dark class="white">
    <!-- <v-app-bar app src="/background.jpg"> -->
    <v-app-bar app hide-on-scroll border outline class="black">
      <v-divider></v-divider>
      <v-card shaped>
        <v-card-title class="title">
          M. Yetisir
        </v-card-title>
      </v-card>
    </v-app-bar>
    <v-navigation-drawer
      ref="navigationDrawer"
      app
      clipped
      permanent
      floating
      hide-overlay
      elevation="0"
      color="transparent"
      width="200"
      mini-variant
      mini-variant-width="75"
    >
      <v-layout column fill-height>
        <v-list> </v-list>
        <v-spacer />
        <v-card
          color="transparent"
          @mouseenter="isMouseOver = true"
          @mouseleave="isMouseOver = false"
        >
          <v-list shaped ref="navigationList">
            <v-list-item
              active-class="title"
              v-for="(item, i) in pages"
              :key="i"
              :to="item.to"
              exact
              @mouseenter="setHoverStatus(i, true)"
              @mouseleave="setHoverStatus(i, false)"
            >
              <v-tooltip nudge-right="10" right color="black">
                <template v-slot:activator="{ on, attrs }">
                  <v-list-item-action v-bind="attrs" v-on="on">
                    <v-icon :x-large="item.hover">{{ item.icon }}</v-icon>
                  </v-list-item-action>
                </template>
                <span>{{ item.title }}</span>
              </v-tooltip>

              <v-list-item-content>
                <v-list-item-title
                  :class="[item.hover ? 'white--text' : '', 'black--text']"
                  v-text="item.title"
                />
              </v-list-item-content>
            </v-list-item>
          </v-list>
        </v-card>
        <v-spacer />
        <v-list> </v-list>
      </v-layout>
    </v-navigation-drawer>

    <v-main>
      <nuxt />
    </v-main>

    <v-footer app>
      <span>&copy; M. Yetisir {{ new Date().getFullYear() }}</span>
    </v-footer>
  </v-app>
</template>

<script>
export default {
  props: {
    navigationDrawerBackgroundSource: {
      type: String,
      default: '/background_2.jpg',
    },
  },
  data() {
    return {
      navigationDrawerOpen: false,
      isMouseOver: false,
      pages: [
        {
          icon: 'mdi-home',
          title: 'Home',
          to: '/',
          hover: false,
        },
        {
          icon: 'mdi-chart-bubble',
          title: 'Projects',
          to: '/projects',
          hover: false,
        },
        {
          icon: 'mdi-newspaper',
          title: 'Publications',
          to: '/publications',
          hover: false,
        },
        {
          icon: 'mdi-contacts',
          title: 'Contact',
          to: '/contact',
          hover: false,
        },
        {
          icon: 'mdi-smoke-detector',
          title: 'Smoke',
          to: '/smoke',
          hover: false,
        },
      ],
      right: true,
      title: 'Vuetify.js',
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
