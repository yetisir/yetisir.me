<template>
  <v-navigation-drawer
    ref="navigationDrawer"
    app
    permanent
    floating
    hide-overlay
    color="transparent"
    mini-variant
    mini-variant-width="65"
  >
    <v-layout column fill-height>
      <v-list> </v-list>
      <v-spacer />
      <v-card color="transparent" outlined>
        <v-list shaped>
          <slot />
        </v-list>
      </v-card>
      <v-spacer />
      <v-list> </v-list>
    </v-layout>
  </v-navigation-drawer>
</template>
