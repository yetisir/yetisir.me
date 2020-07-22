<template>
  <v-container>
    <h1 class="h1">{{ title }}</h1>
    <v-row
      v-for="(job, index) in jobs"
      :key="index"
      justify="center"
      class="ma-6"
    >
      <job
        :title="job.title"
        :employer="job.employer"
        :group="job.group"
        :image="job.image"
        :description="job.description"
        :details="job.details"
        :years="job.years"
      />
    </v-row>
  </v-container>
</template>

<script>
import Job from '@/components/Job'

export default {
  components: {
    Job,
  },
  data() {
    return {
      title: 'Work Experience',
      jobs: [
        {
          employer: 'Golder Associates',
          years: '2017 - 2020',
          // image: '/golder.png',
          group: 'Mine Stability Group',
          title: 'Rock Mechanics Engineer',
          description:
            'Responsible for providing detailed geotechnical engineering designs to mining clients and developing large scale FLAC3D geomechanical models for open pit and underground mines to help predict	deformation and stability of proposed designs.',
          details: [
            'Designed and implemented a Python application for a large open pit mining client which automated routine hydrogeological monitoring and reporting of over 1000 piezometers on site; construction of these reports previously took several weeks annually to prepare.',
            'Developed a Python framework to decrease model build time, verify model integrity, and ensure reproducibility by integrating git version control and substantial automation into modeling workflows; model build time and errors decreased by more than 50%',
            'Managed and automated 100+ GB modeling workflows across Windows and Linux platforms involving hundreds of case permutations and millions of files.',
            'Spearheaded an initiative to coalesce all in-house scripting into a central modular Python library. Reviewed pull requests from contributors and enforced strict testing and documentation on all submissions.',
            'Designed and implemented a Python library based on VTK and SQL to help develop, validate, and visualize 3D computational models for an in-house geomechanics solver including a prototyped job scheduler to manage model runs on an HPC cluster.',
          ],
        },
        {
          employer: 'University of Waterloo',
          years: '2014 - 2017',
          // image: '/uwaterloo.png',
          group: 'WatFrac Research Group',
          title: 'Computational Geomechanics Researcher',
          description:
            'Research focused on practical applications of multi-scale geomechanics, fracture mechanics, and computational homogenization.',
          details: [
            'Developed a discontinuum (UDEC) to continuum (ABAQUS) up-scaling framework for fractured rock masses showing an increase in computational efficiency by up to three orders of magnitude with less than 5% error using a continuum damage mechanics approach.',
            'Implemented the aforementioned up-scaling framework in Python to automate the evaluation of an optimized equivalent continuum response for a given fractured rock mass.',
            'Co-authored a patent application detailing a new methodology for estimating the size of a slurried solid waste injection zone using a novel hydraulic fracturing model.',
          ],
        },
      ],
    }
  },
  head() {
    return {
      title: this.title,
    }
  },
}
</script>
