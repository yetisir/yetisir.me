<template>
  <card
    :title="title"
    :subtitle="employer"
    :bodyText="description"
    :bodyList="details"
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
    details: {
      type: Array,
      default: () => [],
    },
  },
}
</script>
