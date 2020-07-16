<template>
  <!-- <v-app-bar app src="/background.jpg"> -->

  <v-app-bar app hide-on-scroll border outline flat class="transparent">
    <v-divider></v-divider>
    <nuxt-link to="/">
      <v-card
        class="card"
        shaped
        @mouseenter="mouseOver = true"
        @mouseleave="mouseOver = false"
      >
        <v-card-title :class="[mouseOver ? 'glow' : '', 'title']">
          M. Yetisir
        </v-card-title>
      </v-card>
    </nuxt-link>
  </v-app-bar>
</template>
<script>
export default {
  data() {
    return {
      mouseOver: false,
    }
  },
}
</script>
<style>
.title {
  text-decoration: none !important;
  text-align: center;
  text-justify: center;
  font-family: 'Lobster', cursive !important;
  font-size: 25em;
  color: #fff;
  letter-spacing: -7px;
  font-weight: 700;
  text-transform: uppercase;
}
.card {
  background: linear-gradient(
    90deg,
    rgba(50, 50, 50, 1) 0%,
    rgba(0, 0, 0, 1) 100%
  );
}
</style>
