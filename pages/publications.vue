<template>
  <v-container>
    <v-row
      v-for="(publication, index) in publications"
      :key="index"
      justify="center"
      class="ma-6"
    >
      <publication
        :title="publication.title"
        :authors="publication.author"
        :year="getDate(publication)"
        :journal="getJournal(publication)"
      />
    </v-row>
  </v-container>
</template>

<script>
import Cite from 'citation-js'
import bibtexRaw from '@/static/resume/src/sections/bibliography.bib'
import Publication from '@/components/Publication'

export default {
  components: {
    Publication,
  },
  data() {
    return {
      bibtexRaw,
      publications: Cite.input(bibtexRaw),
    }
  },

  methods: {
    getDate(publication) {
      return publication.issued['date-parts'][0][0]
    },
    getJournal(publication) {
      if (publication.type === 'article-journal') {
        if (publication.volume) {
          return publication['container-title'] + ' Vol. ' + publication.volume
        } else {
          return publication['container-title']
        }
      } else if (publication.type === 'paper-conference') {
        return publication['container-title']
      }
    },
  },
}
</script>
