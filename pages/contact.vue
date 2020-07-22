<template>
  <v-container>
    <h1 class="h1">{{ title }}</h1>
    <v-row justify="center" class="ma-6">
      <card title="yetisir@gmail.com" link="mailto:yetisir@gmail.com"> </card>
    </v-row>
    <v-row justify="center" class="ma-6">
      <card title="+1 (858) 336-1186" link="tel:+18583361186"> </card>
    </v-row>
    <v-row justify="center" class="ma-6">
      <quote
        image="/background_8.jpg"
        quote="If you choose not to decide, you still have made a choice."
        author="Neil Peart"
      />
    </v-row>
  </v-container>
</template>
<script>
import Card from '@/components/Card'
export default {
  components: {
    Card,
  },
  data() {
    return {
      title: 'Contact',
    }
  },
  head() {
    return {
      title: this.title,
    }
  },
}
</script>
