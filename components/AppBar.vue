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
      <v-row>
        <v-slide-x-transition hide-on-leave>
          <div v-if="!mouseOver">
            <!-- <nuxt-link to="/"> -->
            <v-btn rounded color="transparent" :class="['title']">
              M. Yetisir
            </v-btn>
            <!-- </nuxt-link> -->
          </div>
        </v-slide-x-transition>
        <v-slide-x-reverse-transition hide-on-leave>
          <v-row v-if="mouseOver" class="ms-3">
            <v-btn
              rounded
              color="transparent"
              href="http://yetisir.me"
              :class="['title']"
            >
              M. Yetisir
            </v-btn>
            <v-btn
              rounded
              color="transparent"
              href="https://github.com/yetisir"
            >
              <v-icon>mdi-github</v-icon>
            </v-btn>
            <v-btn
              rounded
              at
              color="transparent"
              href="https://www.linkedin.com/in/michael-yetisir/"
            >
              <v-icon>mdi-linkedin</v-icon>
            </v-btn>
          </v-row>
        </v-slide-x-reverse-transition>
      </v-row>
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

/* Enter and leave animations can use different */

/* durations and timing functions.              */
.slide-fade-enter-active {
  transition: all 0.3s ease;
}
.slide-fade-leave-active {
  transition: all 0.8s cubic-bezier(1, 0.5, 0.8, 1);
}
.slide-fade-enter, .slide-fade-leave-to

/* .slide-fade-leave-active below version 2.1.8 */ {
  transform: translateX(10px);
  opacity: 0;
}
</style>
