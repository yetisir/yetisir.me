<template>
  <card
    :title="degree"
    :subtitle="description"
    :details="schoolYears"
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
    degree: {
      type: String,
      default: '',
    },
    description: {
      type: String,
      default: '',
    },
    school: {
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
    schoolYears() {
      return `${this.school} [${this.years}]`
    },
  },
}
</script>
