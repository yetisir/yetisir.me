<template>
  <!-- <v-app-bar app src="/background.jpg"> -->

  <v-app-bar app flat border outline color="transparent">
    <v-divider></v-divider>
    <v-card
      class="card"
      rounded="xl"
      elevation="20"
      hide-overlay
      @mouseenter="
        if ($vuetify.breakpoint.width > 400) {
          mouseOver = true
        }
      "
      @mouseleave="mouseOver = false"
    >
      <v-btn
        rounded
        color="transparent"
        href="http://yetisir.me"
        :class="['title']"
      >
        M. Yetisir
      </v-btn>
      <v-expand-x-transition v-for="(link, index) in socialLinks" :key="index">
        <v-hover v-slot:default="{ hover }">
          <v-btn
            v-if="mouseOver"
            :class="[hover ? 'glow' : '']"
            rounded
            color="transparent"
            :href="link.url"
          >
            <v-icon :x-large="hover">{{ link.icon }}</v-icon>
          </v-btn>
        </v-hover>
      </v-expand-x-transition>
    </v-card>
  </v-app-bar>
</template>
<script>
export default {
  data() {
    return {
      mouseOver: false,
      socialLinks: [
        {
          name: 'GitHub',
          url: 'https://github.com/yetisir',
          icon: 'mdi-github',
        },
        {
          name: 'LinkedIn',
          url: 'https://www.linkedin.com/in/michael-yetisir/',
          icon: 'mdi-linkedin',
        },
      ],
    }
  },
  mounted() {
    if (this.$vuetify.breakpoint.width > 400) {
      this.mouseOver = true
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
    rgba(100, 100, 100, 1) 0%,
    rgba(0, 0, 0, 1) 100%
  );
}
</style>
