<template>
  <!-- vue glow module assumes client rendering -->
  <no-ssr>
    <vue-glow color="white" :elevation="mouseOver ? 10 : 0">
      <v-card
        :href="url"
        :loading="loading"
        :img="image"
        width="500"
        target="_blank"
        outlined
        @mouseenter="mouseOver = true"
        @mouseleave="mouseOver = false"
      >
        <v-card-title :class="[mouseOver ? 'glow' : '']">
          {{ title }}
        </v-card-title>
        <slot />
        <!-- <v-overlay v-if="mouseOver" absolute></v-overlay> -->
      </v-card>
    </vue-glow>
  </no-ssr>
</template>

<script>
import VueGlow from 'vue-glow'
export default {
  components: {
    VueGlow,
  },
  props: {
    url: {
      type: String,
      default: '',
    },
    loading: {
      type: Boolean,
      default: false,
    },
    title: {
      type: String,
      default: '',
    },
    image: {
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
.v-card__text,
.v-card__title {
  word-break: normal;
}
</style>
