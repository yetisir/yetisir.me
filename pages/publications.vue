<template>
  <v-container>
    <h1 class="h1">{{ title }}</h1>

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
        :abstract="getAbstract(publication)"
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
      title: 'Publications and Conferences',
      bibtexRaw,
      publications: Cite.input(bibtexRaw),
      // abstracts should be moved to bibtex file when citation.js support abstract field
      abstracts: {
        yetisir2019homogenization:
          'A Distinct Element Method (DEM) up-scaling framework is presented that estimates the parameters of a continuum constitutive model that best captures the salient features of naturally fractured rock (NFR) behaviour. Up-scaling is achieved using homogenized DEM stress–strain curves and a particle swarm optimization algorithm followed by a Levenberg–Marquardt algorithm. The effectiveness of the framework is demonstrated by up-scaling a DEM model of a NFR to a Drucker–Prager damage-plasticity model. The up-scaled continuum model is shown to compare well (<5% error) with direct numerical simulation in a slope stability analysis and requires two orders of magnitude less computational effort.',
        carvalho2019behaviour:
          'Ubiquitous joint constitutive models have been available for numerical analysis for a few decades. However, mis-understanding of the true behavior of these models is still quite prevalent among users. The purpose and goal of addressing strength anisotropy through a ubiquitous joint model embedded in a constitutive model has been successful, but the deformations do not follow the intuitive behaviour in many cases. This paper dissects the constitutive formulation of the ubiquitous joint model and compares its behaviour against explicitly modelled joint networks to show the range of applicability of ubiquitous joint models and when they fall short of capturing the correct deformation behaviour. The paper will show that ubiquity does not equate to continuity and that ubiquitous joint models are not able to capture the correct behaviour for discontinuities of large extent, such as bedding or faults. The paper will also show that this behaviour is inherent in the incremental stress/strain formulation of constitutive models and not specific to any finite element or finite difference code.',
        lawrence2019variants: '',
        yetisir2019assessment: '',
        yetisir2019coupled: '',
        cambio2019back:
          'A 610-m-high portion of the South Wall of the Bingham Canyon open pit has experienced slow-moving slope deformations several times during spring melt until the movement was stabilized approximately 7 years ago. To develop and optimize life of mine slope designs, an understanding of the mechanism(s) and associated material strength parameters, was required. A back-analysis and calibration of the strength parameters for the salient rock mass and structural features was undertaken. The back-analysis consisted of understanding the conditions and trigger for the slope movement and adjusting strength parameters to match available monitoring data (time-domain reflectometer cables, inclinometers, interferometric radar data, etc.). The trigger for the movement was attributed to the spring high-perched water levels in the upper part of the wall. A FLAC3D model was built to back-analyze and capture the complex behavior of the slope during the high deformation period (August 2011). The back-analysis was consistent with the conceptual model and indicated that the slide was composed of mixed mechanisms, namely, a structurally controlled mechanism for the upper wall and a rock mass controlled mechanism for the lower wall (toe). The analysis supported by a converging FLAC3D model, were used to guide mining engineers in developing robust pit design in the South Wall. Today, the O-Slide instability is being fully managed by rigorous monitoring, implementation of a toe buttress, successful dewatering efforts, and unloading of the movement mass as another slice of mining advances down the South Wall.',
        moffitt2018back:
          'A 610 m (2000 foot) high portion of the South Wall of the Bingham Canyon open pit has experienced slow-moving slope deformations several times during spring melt until the movement was stabilized approximately 7 years ago. To develop and optimize life of mine (LOM) slope designs, an understanding of the mechanism(s) and associated material strength parameters, was required. A back-analysis and calibration of the strength parameters for the salient rock mass and structural features was undertaken. The back-analysis consisted of understanding the conditions and trigger for the slope movement and adjusting strength parameters to match available monitoring data (TDR cables, inclinometers, IBIS radar data, etc.). The trigger for the movement was attributed to the spring high-perched water levels in the upper part of the wall. The back-analyses was consistent with the conceptual model and indicated that the slide was composed of mixed mechanisms, namely, a structurally controlled mechanism for the upper wall and a rock mass controlled mechanism for the lower wall (toe). Today, the O-Slide instability has been fully managed by rigorous monitoring, implementation of a toe buttress, successful dewatering efforts, and unloading of the movement mass as another slice of mining advanced down the South Wall.',
        yetisir2017up:
          'Pre-existing fractures significantly influence the geomechanical response of the rock mass at the reservoir scale. For geomechanical applications, these natural fractures need to be considered in the mechanical response of the system. Distinct Element Methods (DEM) are often used to explicitly model the mechanics of Naturally Fractured Rock (NFR); however, they are often too computationally prohibitive for reservoir-scale problems. A DEM up-scaling framework is presented that facilitates estimating a representative parameter set for continuum constitutive models that capture the salient feature of Naturally Fractured Rock (NFR) behaviour. Up-scaling is achieved by matching homogenized DEM stress-strain curves from multiple load paths to those of continuum constitutive models using a Particle Swarm Optimization (PSO) algorithm followed by a Damped Least-Squares (DLS) algorithm. The effectiveness of the framework is demonstrated by up-scaling a DEM model of a NFR to a Drucker-Prager damage-plasticity model; the up-scaled model is shown to capture well the effect of confinement on the the yielding and sliding of natural fractures in the rock mass. The goal of this thesis is to present a framework to facilitate effective simulation of fine-scale behaviour in full-scale NFR systems while significantly reducing the computational demands associated with modelling these systems with DEM. As such, four main research objectives have been identified and achieved: 1) Develop and implement stress and strain homogenization algorithms for DEM models with deformable blocks, 2) present a methodology to parameterize complex nonlinear continuum constitutive models, 3) develop and implement an automated modular software framework for up-scaling DEM simulations, and 4) demonstrate that the performance of the up-scaled continuum models are accurate and significantly more computationally efficient. The up-scaling methodology is verified through a case study on a naturally fractured granite slope in which the top surface is loaded until failure. The up-scaled continuum model is shown to compare quite well to Direct Numerical Simulation (DNS) in a slope stability analysis and requires two orders of magnitude less computational effort.',
        yetisir2016up:
          'Discrete Element Methods (DEM) explicitly model the mechanics of the discontinuities of naturally fractured rock masses. However, due to the large number of degrees of freedom in DEM simulations and the requirement of small times steps, the application of DEM simulations to reservoir-scale problems and long-term fluid injection problems is often computationally prohibitive. In order to reduce the computational costs associated with full-scale DEM simulations, an up-scaling method is presented in which Representative Elementary Volume (REV) DEM simulations are used to calibrate the parameters of a Continuum Damage Mechanics (CDM) constitutive model that is then used for Finite Element Analysis (FEA). The CDM model empirically captures the effect of the degradation of the rock integrity due to the yielding and sliding of natural fractures in the rock mass. Up-scaling is achieved through homogenization, in which the spatially averaged stress-strain behavior of various DEM RVE simulations is computed. Subsequently, a CDM constitutive relationship is fitted using the Levenberg-Marquardt Algorithm (LMA) and the homogenized DEM simulation data. The CDM model is then used in FEA reservoir scale simulations. The CDM model is implemented in ABAQUSTM and DEM simulations were conducted using UDECTM. The up-scaling methodology is demonstrated through a case study on a naturally fractured carbonate reservoir in which the up-scaled CDM model compares well with a direct numerical simulation with the DEM model but requires an order of magnitude less computational time.',
      },
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
    getAbstract(publication) {
      return this.abstracts[publication.id]
    },
  },
  head() {
    return {
      title: this.title,
    }
  },
}
</script>
