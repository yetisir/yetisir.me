<template>
  <card :title="degree" :subtitle="school" :body-list="details" :image="image">
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
    degree: {
      type: String,
      default: '',
    },
    school: {
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
