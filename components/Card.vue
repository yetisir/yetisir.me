<template>
  <no-ssr>
    <v-card
      :class="[mouseOver ? 'shadow' : '', 'parent']"
      :loading="loading"
      :img="image"
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
            <v-icon v-if="mouseOver">{{ urlIcon }}</v-icon>
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
              <v-icon v-if="showBody">mdi-arrow-collapse-all</v-icon>
              <v-icon v-else>mdi-arrow-expand-all</v-icon>
            </div>
          </v-btn>
        </v-hover>
      </v-card-title>

      <v-card-subtitle> {{ subtitle }} </v-card-subtitle>

      <v-expand-transition>
        <v-card v-if="showBody" class="cardbody ma-3 pa-3" outlined>
          <vue-markdown>
            {{ body }}
          </vue-markdown>
        </v-card>
      </v-expand-transition>
      <slot />
    </v-card>
  </no-ssr>
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
    body: {
      type: String,
      default: '',
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

.cardbody {
  opacity: 0.8;
}
</style>
