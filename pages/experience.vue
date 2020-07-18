<template>
  <v-timeline>
    <v-timeline-item v-for="(item, i) in items" :key="i" right>
      <template v-slot:icon>
        <v-avatar v-if="avatar">
          <img src="http://i.pravatar.cc/64" />
        </v-avatar>
      </template>
      <template v-slot:opposite>
        <span class="headline font-weight-bold" v-text="2020"></span>
      </template>
      <card :color="item.color" dark>
        <v-card-title class="title">Lorem Ipsum Dolor</v-card-title>
        <v-card-text>
          <p>
            Lorem ipsum dolor sit amet, no nam oblique veritus. Commune scaevola
            imperdiet nec ut, sed euismod convenire principes at. Est et nobis
            iisque percipit, an vim zril disputando voluptatibus, vix an
            salutandi sententiae.
          </p>
          <v-btn :color="item.color" class="mx-0" outlined>
            Button
          </v-btn>
        </v-card-text>
      </card>
    </v-timeline-item>
  </v-timeline>
</template>

<script>
import Card from '@/components/Card'

export default {
  components: {
    Card,
  },
  data: () => ({
    items: [
      {
        color: 'red lighten-2',
        icon: 'mdi-star',
      },
      {
        color: 'purple darken-1',
        icon: 'mdi-book-variant',
      },
      {
        color: 'green lighten-1',
        icon: 'mdi-airballoon',
      },
      {
        color: 'indigo',
        icon: 'mdi-buffer',
      },
    ],
  }),
}
</script>
<style>
.v-timeline-item__opposite .v-timeline--dense {
  display: inline-block;
}

.v-timeline-item__opposite .v-timeline-item--left .v-timeline-item__opposite,
.v-timeline-item:nth-child(odd):not(.v-timeline-item--right) {
  margin-left: 16px;
  margin-right: 86px;
}

.v-timeline-item__opposite .v-timeline-item--right .v-timeline-item__opposite,
.v-timeline-item:nth-child(2n):not(.v-timeline-item--left) {
  margin-left: 16px;
  margin-right: 86px;
  text-align: left;
}

.v-timeline--dense::before {
  left: 110px;
}
.v-timeline--dense .v-timeline-item__dot--small {
  left: 99px;
}
</style>
