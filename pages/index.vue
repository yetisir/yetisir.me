<template>
  <v-container>
    <v-row justify="center">
      <v-card width="500" class="profile"> </v-card>
    </v-row>
    <v-row justify="center" class="ma-6">
      <card
        title="M. Yetisir, MASc"
        subtitle="Computational Mechanics Engineer, Software Developer"
        details="Computational geomechanics engineer with 6 years of experience modelling complex solid mechanics problems and	leveraging Python to develop automated and reproducible analysis pipelines."
      ></card>
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
      title: 'Home',
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
.profile {
  width: 500px;
  height: 500px;
  position: relative;
  background: radial-gradient(
      circle,
      rgba(255, 255, 255, 0) 0%,
      rgba(255, 255, 255, 0) 40%,
      rgba(255, 255, 255, 1) 50%,
      rgba(255, 255, 255, 1) 100%
    ),
    url('/background_9.jpg');
  background-position: 60% 20%;
  mask-image: radial-gradient(
    circle,
    rgba(255, 255, 255, 1) 0%,
    rgba(255, 255, 255, 1) 20%,
    rgba(0, 0, 0, 0) 55%,
    rgba(0, 0, 0, 0) 100%
  );
}
</style>
