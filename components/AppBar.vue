<template>
  <!-- <v-app-bar app src="/background.jpg"> -->

  <v-app-bar app hide-on-scroll border outline color="transparent">
    <v-divider></v-divider>
    <v-card
      class="card"
      rounded="xl"
      elevation="20"
      hide-overlay
      @mouseenter="mouseOver = true"
      @mouseleave="mouseOver = false"
    >
      <!-- <v-row>
        <v-slide-x-transition hide-on-leave>
          <div v-if="!mouseOver">
            <v-btn rounded color="transparent" :class="['title']">
              M. Yetisir
            </v-btn>
          </div>
        </v-slide-x-transition>
      </v-row> -->

      <v-btn
        rounded
        color="transparent"
        href="http://yetisir.me"
        :class="['title']"
      >
        M. Yetisir
      </v-btn>
      <v-expand-x-transition>
        <v-btn
          v-if="mouseOver"
          rounded
          color="transparent"
          href="https://github.com/yetisir"
        >
          <v-icon>mdi-github</v-icon>
        </v-btn>
      </v-expand-x-transition>
      <v-expand-x-transition>
        <v-btn
          v-if="mouseOver"
          rounded
          at
          color="transparent"
          href="https://www.linkedin.com/in/michael-yetisir/"
        >
          <v-icon>mdi-linkedin</v-icon>
        </v-btn>
      </v-expand-x-transition>
    </v-card>
    <!-- <v-card v-if="mouseOver" href="facebook.com"> -->
    <!-- </v-card> -->
    <!-- <v-card v-if="mouseOver" href="linkedin.com"> -->
    <!-- </v-card> -->
    <!-- </v-row> -->
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
    rgba(100, 100, 100, 1) 0%,
    rgba(0, 0, 0, 1) 100%
  );
}
</style>
