<template>
  <card :title="yearTitle" :subtitle="journal" :body="abstract">
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
  </card>
</template>

<script>
import Card from '@/components/Card'
export default {
  components: {
    Card,
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
    abstract: {
      type: String,
      default: '',
    },
  },

  data() {
    return {
      mouseOver: false,
      loading: false,
      url: '',
      urlIcon: '',
    }
  },
  computed: {
    yearTitle() {
      return `[${this.year}] ${this.title}`
    },
  },
}
</script>
<style>
.v-card__text,
.v-card__title {
  word-break: normal;
}
</style>
