<template>
  <v-list-item
    :to="route"
    active-class="glow"
    @mouseenter="mouseOver = true"
    @mouseleave="mouseOver = false"
  >
    <v-tooltip nudge-right="10" right color="black">
      <template v-slot:activator="{ on, attrs }">
        <v-list-item-action
          v-bind="attrs"
          v-on="on"
          :class="[mouseOver ? 'glow' : '', 'black--text']"
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
.glow {
  text-align: center;
  text-justify: center;
  font-size: 25em;
  color: #fff;
  letter-spacing: -7px;
  font-weight: 700;
  text-transform: uppercase;
  text-shadow: 0 0 5px #fff, 0 0 7px #fff;
}
</style>
