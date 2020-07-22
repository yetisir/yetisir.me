<template>
  <v-card
    :class="[mouseOver ? 'shadow cardmain' : '', 'parent']"
    :loading="loading"
    :img="image"
    :style="style"
    :href="link"
    width="500"
    target="_blank"
    outlined
    @mouseenter="mouseOver = true"
    @mouseleave="mouseOver = false"
  >
    <v-card-title>
      {{ title }}
      <v-spacer />
      <v-hover v-slot:default="{ hover }">
        <v-btn v-if="urlIcon" icon :class="[hover ? 'glow' : '']" :href="url">
          <v-icon v-if="mouseOver" :x-large="hover">{{ urlIcon }}</v-icon>
        </v-btn>
      </v-hover>

      <v-hover v-slot:default="{ hover }">
        <v-btn
          v-if="body"
          icon
          :class="[hover ? 'glow' : '']"
          @click="showBody = !showBody"
        >
          <div v-if="mouseOver">
            <v-icon v-if="showBody" :x-large="hover">
              mdi-arrow-collapse-all</v-icon
            >
            <v-icon v-else :x-large="hover">mdi-arrow-expand-all</v-icon>
          </div>
        </v-btn>
      </v-hover>
    </v-card-title>

    <v-card-subtitle class="font-italic font-weight-bold">
      {{ subtitle }}
    </v-card-subtitle>
    <v-card-text v-if="details"> {{ details }} </v-card-text>

    <v-container v-if="tags.length">
      <v-row>
        <v-card
          v-for="(tag, index) in tags"
          :key="index"
          class="ma-1 py-0 translucent"
          outlined
        >
          <v-card-subtitle class="py-2">
            {{ tag }}
          </v-card-subtitle>
        </v-card>
      </v-row>
    </v-container>

    <v-expand-transition>
      <v-card v-if="showBody" class="translucent ma-3 pa-3" outlined>
        <vue-markdown v-if="bodyMd">{{ bodyMd }}</vue-markdown>
        <v-card-text v-if="bodyText">{{ bodyText }}</v-card-text>
        <ul v-if="bodyList.length">
          <li v-for="(item, i) in bodyList" :key="i" class="mb-5">
            {{ item }}
          </li>
        </ul>
      </v-card>
    </v-expand-transition>
    <slot />
  </v-card>
</template>

<script>
import VueMarkdown from 'vue-markdown'

export default {
  components: {
    VueMarkdown,
  },
  props: {
    url: {
      type: String,
      default: '',
    },
    urlIcon: {
      type: String,
      default: '',
    },
    link: {
      type: String,
      default: '',
    },
    loading: {
      type: Boolean,
      default: false,
    },
    title: {
      type: String,
      default: '',
    },
    subtitle: {
      type: String,
      default: '',
    },
    details: {
      type: String,
      default: '',
    },
    tags: {
      type: Array,
      default: () => [],
    },
    bodyText: {
      type: String,
      default: '',
    },
    bodyMd: {
      type: String,
      default: '',
    },
    bodyList: {
      type: Array,
      default: () => [],
    },
    image: {
      type: String,
      default: '',
    },
  },
  data() {
    return {
      mouseOver: false,
      showBody: false,
    }
  },
  computed: {
    body() {
      return Boolean(this.bodyText || this.bodyMd || this.bodyList.length)
    },
    style() {
      if (this.mouseOver) {
        return `background: linear-gradient(90deg, rgb(0, 0, 0) 0%, rgb(0, 0, 0) 40%, ${this.color} 50%, rgb(0, 0, 0) 60%, rgb(0, 0, 0) 100%); background-size: 350% 100%; animation: gradient 3s linear infinite reverse;`
      } else {
        return 'background: black'
      }
    },
    color() {
      function randomVal(min, max) {
        return Math.floor(Math.random() * (max - min) + 1) + min
      }
      return (
        'hsl(' +
        randomVal(0, 360) +
        ', ' +
        randomVal(30, 95) +
        '%,  ' +
        randomVal(10, 20) +
        '%)'
      )
      // return '#' + Math.floor(Math.random() * 16777215).toString(16)
    },
  },
}
</script>
<style>
.v-card__text,
.v-card__title {
  word-break: normal;
}

.shadow {
  box-shadow: 0 4px 8px 0 rgba(255, 255, 255, 0.2),
    0 6px 20px 0 rgba(255, 255, 255, 0.19) !important;
}

.translucent {
  opacity: 0.8;
}

@keyframes gradient {
  0% {
    background-position: 0% 50%;
  }
  100% {
    background-position: 100% 50%;
  }
}
</style>
