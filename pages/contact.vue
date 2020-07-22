<template>
  <v-container>
    <h1 class="h1">Contact</h1>
    <card class="my-5" title="yetisir@gmail.com"> </card>
  </v-container>
</template>
<script>
import Card from '@/components/Card'
export default {
  components: {
    Card,
  },
  head() {
    return {
      title: this.title,
    }
  },
}
</script>
