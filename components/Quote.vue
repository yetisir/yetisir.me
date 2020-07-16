<template>
  <v-card width="500" color="black">
    <v-img :src="image"> </v-img>
    <v-card-title class="font-weight-light">
      &#8220;If you choose not to decide, you still have made a choice.&#8221;
    </v-card-title>
    <v-card-subtitle class="text-right">
      <em>&mdash;Neil Peart</em>
    </v-card-subtitle>
  </v-card>
</template>

<script>
export default {
  props: {
    image: {
      type: String,
      default: '',
    },
    quote: {
      type: String,
      default: '',
    },
    author: {
      type: String,
      default: '',
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
