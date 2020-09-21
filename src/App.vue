<template>
  <div id="main">
    <MainHero />
    <Navbar :elements="elements"/>
    <div class="relative min-h-screen md:left-64 md:fix-width">
      <Projects />
      <Skills />
      <Achievements />
    </div>
  </div>
</template>

<script>
import MainHero from './components/MainHero.vue'
import Navbar from './components/Navbar'
import Projects from './components/Projects'
import Skills from './components/Skills'
import Achievements from './components/Achievements'

export default {
  name: 'App',
  components: {
    MainHero,
    Navbar,
    Projects,
    Skills,
    Achievements
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
