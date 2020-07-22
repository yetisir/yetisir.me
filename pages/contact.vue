<template>
  <v-container>
    <h1 class="h1">{{ title }}</h1>
    <v-row justify="center" class="ma-6">
      <card title="yetisir@gmail.com" link="mailto:yetisir@gmail.com"> </card>
    </v-row>
    <v-row justify="center" class="ma-6">
      <card title="+1 (858) 336-1186" link="tel:+18583361186"> </card>
    </v-row>
    <v-row justify="center">
      <v-card width="500" class="picture"> </v-card>
    </v-row>
    <v-row justify="center">
      <v-card color="transparent">
        <v-card-title class="font-weight-light">
          &#8220;If you choose not to decide, you still have made a
          choice.&#8221;
        </v-card-title>
        <v-card-subtitle class="text-right">
          <em>&mdash;Neil Peart</em>
        </v-card-subtitle>
      </v-card>
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
<style>
.picture {
  width: 500px;
  height: 500px;
  position: relative;
  background: url('/background_6.jpg');
  background-size: 300%;
  background-position: 50% 50%;
  mask-image: radial-gradient(
    circle,
    rgba(255, 255, 255, 1) 0%,
    rgba(255, 255, 255, 1) 20%,
    rgba(0, 0, 0, 0) 55%,
    rgba(0, 0, 0, 0) 100%
  );
}
</style>
