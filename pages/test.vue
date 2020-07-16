<template>
  <v-container>
    <v-row justify="center" class="ma-6">
      <quote :image="image" :quote="quote" :author="author" />
    </v-row>
  </v-container>
</template>

<script>
import Quote from '@/components/Quote'

export default {
  components: {
    Quote,
  },
  data() {
    return {
      image: '/background_8.jpg',
      quote: 'If you choose not to decide, you still have made a choice.',
      author: 'Neil Peart',
    }
  },
}
</script>
