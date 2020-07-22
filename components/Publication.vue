<template>
  <card :title="title" :subtitle="yearJournal" :body="abstract" :tags="tags">
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
    yearJournal() {
      return `${this.journal} [${this.year}] `
    },
    tags() {
      return this.authors.map((author) => `${author.family}, ${author.given}`)
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
