<template>
  <v-container>
    <h1 class="h1">Work Experience</h1>

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
      jobs: [
        {
          employer: 'Golder Associates',
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
          // image: '/uwaterloo.png',
          group: 'WatFrac Research Group',
          title: 'Computational Geomechanics Researcher',
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
      ],
    }
  },
}
</script>

<style>
/* .v-timeline--dense .v-timeline-item__opposite {
  text-align: right;
  display: inline-block;
}

.v-timeline--dense .v-timeline-item__body {
  text-align: left;
  margin-right: 20px;
  max-width: calc(100% - 250px);
}

.v-timeline--dense.theme--dark::before {
  left: 180px !important;
} */

/* 
.v-timeline-item--left .v-timeline-item__opposite,
.v-timeline-item:nth-child(odd):not(.v-timeline-item--right)
  .v-timeline-item__opposite {
  margin-right: 86px;
}
.v-timeline-item--right .v-timeline-item__opposite,
.v-timeline-item:nth-child(2n):not(.v-timeline-item--left)
  .v-timeline-item__opposite {
  margin-left: 16px;
  margin-right: 86px;
  text-align: left;
}

.v-timeline--dense:before {
  left: 110px;
}
.v-timeline--dense .v-timeline-item__dot--small {
  left: 99px;
} */
</style>
