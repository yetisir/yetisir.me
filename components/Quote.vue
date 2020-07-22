<template>
  <v-card color="transparent">
    <v-card class="picture" width="500">
      <v-img :src="image"> </v-img>
    </v-card>
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

.picture {
  width: 500px;
  height: 500px;
  position: relative;
  background-position: 60% 30%;
  mask-image: radial-gradient(
    circle,
    rgba(255, 255, 255, 1) 0%,
    rgba(255, 255, 255, 1) 20%,
    rgba(0, 0, 0, 0) 55%,
    rgba(0, 0, 0, 0) 100%
  );
}
</style>
