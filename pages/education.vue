<template>
  <v-container>
    <h1 class="h1">{{ title }}</h1>

    <v-row
      v-for="(degree, index) in degrees"
      :key="index"
      justify="center"
      class="ma-6"
    >
      <degree
        :degree="degree.degree"
        :school="degree.school"
        :details="degree.details"
      />
    </v-row>
  </v-container>
</template>

<script>
import Degree from '@/components/Degree'

export default {
  components: {
    Degree,
  },
  data() {
    return {
      title: 'Education',
      degrees: [
        {
          degree: 'Master of Applied Science (Civil Engineering)',
          school: 'University of Waterloo (2009 - 2014)',
          details: [
            'MASc Thesis: Up-Scaling Discrete Element Method Simulations of Discontinua',
            'Awards and Scholarships: Queen Elizabeth Scholarship in Science and Technology, President’s Athlete Academic Award for Outstanding Academic Performance',
          ],
        },
        {
          degree: 'Bachelor of Applied Science (Geological Engineering)',
          school: 'University of Waterloo (2014 - 2016)',
          details: [
            'BASc Thesis: Investigating the Influence of Rock Fabric and Operational Parameters on Hydraulic Fracture Propagation',
            'Awards and Scholarships: Sanford Flemming Award for Cooperative Proficiency, Engineering Upper Year Scholarship for Academic Excellence',
          ],
        },
      ],
      jobs: [
        {
          employer: 'Golder Associates (2017 - 2020) ',
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
          employer: 'University of Waterloo (2014 - 2017)',
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
