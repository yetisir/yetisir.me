<template>
  <v-card
    width="500"
    :href="url"
    target="_blank"
    elevation="20"
    outlined
    :loading="loading"
    @mouseenter="mouseOver = true"
    @mouseleave="mouseOver = false"
  >
    <v-card-title :class="[mouseOver ? 'glow' : '']"
      >[{{ year }}] {{ title }}
    </v-card-title>
    <v-row class="pa-4">
      <v-card v-for="(author, index) in authors" :key="index">
        <v-card-subtitle>
          {{ author.family }}, {{ author.given }}
        </v-card-subtitle>
      </v-card>
    </v-row>

    <!-- <v-card-text>
      {{ abstract }}
    </v-card-text> -->

    <v-overlay v-if="mouseOver" absolute></v-overlay>
  </v-card>
</template>

<script>
export default {
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
  },
  data() {
    return {
      isMouseover: false,
      loading: false,
      url: '',
    }
  },
}
</script>
