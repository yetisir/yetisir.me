<template>
  <vue-glow color="white" :elevation="mouseOver ? 10 : 0">
    <v-card
      width="500"
      :href="url"
      target="_blank"
      outlined
      :loading="loading"
      @mouseenter="mouseOver = true"
      @mouseleave="mouseOver = false"
    >
      <!-- <vue-glow><v-card-title>Test</v-card-title></vue-glow> -->

      <v-card-title :class="[mouseOver ? 'glow' : '']"
        >[{{ year }}] {{ title }}
      </v-card-title>
      <v-card-subtitle>
        {{ journal }}
      </v-card-subtitle>
      <v-container>
        <v-row>
          <v-card
            v-for="(author, index) in authors"
            :key="index"
            class="ma-1 py-0"
            outlined
          >
            <v-card-subtitle>
              {{ author.family }}, {{ author.given }}
            </v-card-subtitle>
          </v-card>
        </v-row>
      </v-container>

      <!-- <v-card-text>
      {{ abstract }}
    </v-card-text> -->

      <v-overlay v-if="mouseOver" absolute></v-overlay>
    </v-card>
  </vue-glow>
</template>

<script>
import VueGlow from 'vue-glow'

export default {
  components: {
    VueGlow,
  },
  props: {
    title: {
      type: String,
      default: '',
    },
    authors: {
      type: Array,
      default: () => [],
    },
    year: {
      type: String,
      default: '',
    },
    journal: {
      type: String,
      default: '',
    },
  },
  data() {
    return {
      mouseOver: false,
      loading: false,
      url: '',
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
