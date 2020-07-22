<template>
  <card
    :title="title"
    :subtitle="employerYears"
    :details="description"
    :body-list="details"
    :image="image"
  >
  </card>
</template>

<script>
import Card from '@/components/Card'

export default {
  components: {
    Card,
  },
  props: {
    image: {
      type: String,
      default: '',
    },
    title: {
      type: String,
      default: '',
    },
    employer: {
      type: String,
      default: '',
    },
    group: {
      type: String,
      default: '',
    },
    description: {
      type: String,
      default: '',
    },
    years: {
      type: String,
      default: '',
    },
    details: {
      type: Array,
      default: () => [],
    },
  },
  computed: {
    employerYears() {
      return `${this.employer} - ${this.group} [${this.years}]`
    },
  },
}
</script>
