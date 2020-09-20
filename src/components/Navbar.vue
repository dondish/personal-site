<template>
  <div class="flex flex-col fixed bg-opacity-90 bg-teal-500 md:pt-4 h-18 w-full md:h-screen md:w-64 left-0 top-0 z-40" :class="toggledNav ? 'h-screen' : 'h-18'">
    <div class="flex flex-row justify-center">
      <div class="md:hidden ml-4 w-8"></div>
      <div class="md:hidden flex-1"></div>
      <img class="ml-2 md:ml-0 h-16 w-16 md:h-32 md:w-32" :src="logo">
      <div class="md:hidden flex-1"></div>
      <div class="md:hidden self-center mr-4">
        <button class="px-3 py-2 rounded text-center text-white" @click="toggleNav()"><i class="fa-w-8 fas fa-bars"></i></button>
      </div>
    </div>
    <div class="flex-col h-full" :class="toggledNav ? 'flex' : 'hidden md:flex'">
      <div class="text-center mt-5 text-white md:text-lg" v-for="(element, idx) in elements" :key="idx">
          <a class="uppercase font-bold" :href="'#'+element.id" @click="toggleNav()">{{ element.name }}</a>
      </div>
      <div class="flex-1"></div>
      <div class="text-center py-4">
        <span class="text-white">Oded Shapira © 2020</span>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Navbar',
  props: ['elements'],
  data () {
    return {
      logo: 'https://avatars0.githubusercontent.com/u/32619328?s=460&u=388d8c809ad57be94e7d7c96d497ca56a1a7d345&v=4',
      toggledNav: false
    }
  },
  methods: {
    toggleNav () {
      this.toggledNav = !this.toggledNav
    }
  }
}
</script>
