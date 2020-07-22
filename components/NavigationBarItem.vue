<template>
  <v-list-item
    :to="route"
    active-class="fade glow"
    @mouseenter="mouseOver = true"
    @mouseleave="mouseOver = false"
  >
    <v-tooltip
      v-if="$vuetify.breakpoint.width > 400"
      nudge-right="15"
      right
      color="black"
    >
      <template v-slot:activator="{ on, attrs }">
        <v-list-item-action
          :class="[mouseOver ? 'glow' : '', 'black--text']"
          v-bind="attrs"
          v-on="on"
        >
          <v-icon :x-large="mouseOver">{{ icon }}</v-icon>
        </v-list-item-action>
      </template>
      <span>{{ name }}</span>
    </v-tooltip>
  </v-list-item>
</template>

<script>
export default {
  props: {
    icon: {
      type: String,
      default: '',
    },
    name: {
      type: String,
      default: '',
    },
    route: {
      type: String,
      default: '',
    },
  },

  data() {
    return {
      mouseOver: false,
    }
  },
}
</script>
<style>
.fade {
  background: linear-gradient(
    90deg,
    rgba(255, 255, 255, 0) 0%,
    rgba(255, 255, 255, 1) 100%
  );
}
</style>
