<template>
  <div id="main">
    <MainHero />
    <Navbar :elements="elements"/>
    <div class="relative min-h-screen md:left-64 md:fix-width">
      <Projects />
      <div id="skills" class="pt-20 md:pt-8 ml-4 text-center">
        <h1 class="text-4xl font-bold">Skills</h1>
      </div>
      <div id="achievements" class="pt-20 md:pt-8 ml-4 text-center">
        <h1 class="text-4xl font-bold">Achievements</h1>
      </div>
    </div>
  </div>
</template>

<script>
import MainHero from './components/MainHero.vue'
import Navbar from './components/Navbar'
import Projects from './components/Projects'

export default {
  name: 'App',
  components: {
    MainHero,
    Navbar,
    Projects
  },
  data () {
    return {
      elements: [
        {
          name: 'home',
          id: ''
        },
        {
          name: 'projects',
          id: 'projects'
        },
        {
          name: 'skills',
          id: 'skills'
        },
        {
          name: 'achievements',
          id: 'achievements'
        }
      ]
    }
  }
}
</script>

<style>
html {
  scroll-behavior: smooth;
}

@layer base {

  @responsive {
    .fix-width {
      width: calc(100% - 16rem);
    }
  }
}
</style>
