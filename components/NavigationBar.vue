<template>
  <v-navigation-drawer
    ref="navigationDrawer"
    app
    permanent
    floating
    hide-overlay
    color="transparent"
    mini-variant
    mini-variant-width="60"
  >
    <v-layout column fill-height>
      <v-list> </v-list>
      <v-spacer />
      <v-card color="transparent" outlined>
        <v-list shaped>
          <navigation-bar-item
            v-for="(page, i) in pages"
            :key="i"
            :route="page.route"
            :icon="page.icon"
            :name="page.name"
          >
          </navigation-bar-item>
        </v-list>
      </v-card>
      <v-spacer />
      <v-list> </v-list>
    </v-layout>
  </v-navigation-drawer>
</template>

<script>
import NavigationBarItem from '@/components/NavigationBarItem'
export default {
  components: {
    NavigationBarItem,
  },
  props: {
    pages: {
      type: Array,
      default: () => [],
    },
  },
}
</script>
