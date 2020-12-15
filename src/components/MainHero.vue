<template>
  <div class="flex flex-col relative h-screen bg-teal-500 lg:p-16 z-50 justify-center">
      <div class="lg:shadow-lg text-center lg:text-left w-full lg:container block lg:grid lg:grid-cols-4 bg-teal-700 lg:rounded pt-12 lg:pt-8 p-8 gap-3 h-screen lg:h-auto lg:mx-auto">
          <div class="flex lg:flex-col justify-center lg:grid-cell lg:col-span-1">
              <div class="lg:flex-1"></div>
              <div class="flex justify-center">
                <img class="h-48 w-48" alt="Dondish" :src="logo">
              </div>
              <div class="lg:flex-1"></div>
          </div>
          <div class="justify-center lg:justify-none lg:col-span-3">
              <h1 class="lg:inline align-baseline mt-2 lg:my-2 text-white text-2xl lg:text-5xl">Oded Shapira</h1>
              <span class="lg:inline mb-6 lg:ml-2 align-baseline text-xl lg:text-3xl text-gray-300">Also known as Dondish</span>
              <h2 class="text-white mb-8 text-l lg:text-3xl">{{scribbledText}}</h2>
              <p class="mb-4 text-white font-mono text-justify">Hello and welcome to my site!<br>I am Oded, known online as Dondish, and I like coding, music and playing video games!</p>
              <div id="buttonList" class="grid grid-cols-2 gap-3 lg:block">
                <a v-for="button of buttons" :key="button.icon" :title="button.name" class="grid-col-span-1 lg:inline-block border border-teal-900 lg:mr-5 hover:text-gray-500 py-2 px-4 bg-teal-800 rounded text-white" :href="button.link"><i class="fa-w-16 fa-2x" :class="(button.style ? button.style : 'fab') + ' fa-'+button.icon"></i></a>
              </div>
          </div>
      </div>
      <div class="absolute h-10 lg:h-16 inset-x-0 bottom-0 text-center text-white animate-bounce">
        <i class="fa-w-16 fa-2x fas fa-chevron-down"></i>
      </div>
  </div>
</template>

<script>
export default {
  name: 'MainHero',
  data () {
    return {
      logo: '/oded.png',
      scribbledText: '',
      scribbleInterval: null,
      scribbleIndex: 0,
      scribbleDataset: [
        'Fullstack Developer',
        'EDM Producer',
        'Data Science Nerd',
        'Enthusiastic Gamer',
        'Cybersecurity Fan',
        'Algorithm Designer',
        'Web developer',
        'Computer Science Lover'
      ],
      buttons: [
        {
          icon: 'envelope',
          name: 'Email',
          link: 'mailto:odedshapira1@protonmail.com',
          style: 'fas'
        },
        {
          icon: 'discord',
          name: 'Discord',
          link: 'https://discord.gg/pEKkg9r'
        },
        {
          icon: 'steam',
          name: 'Steam',
          link: 'https://steamcommunity.com/id/meetyourdeath'
        },
        {
          icon: 'twitter',
          name: 'Twitter',
          link: 'https://twitter.com/dondishdev'
        },
        {
          icon: 'github',
          name: 'GitHub',
          link: 'https://github.com/dondish'
        },
        {
          icon: 'linkedin',
          name: 'LinkedIn',
          link: 'https://www.linkedin.com/in/oded-shapira-b37163188/'
        }
      ]
    }
  },
  methods: {
    startScribbling () {
      this.scribbledText = this.scribbleDataset[this.scribbleIndex] // initialize with the first dataset entry

      this.scribbleInterval = setInterval(async () => {
        await this.animateScribble()
        this.scribbleIndex = (this.scribbleIndex + 1) % this.scribbleDataset.length
      }, 5000)
    },
    async animateScribble () {
      const from = this.scribbleDataset[this.scribbleIndex]
      const to = this.scribbleDataset[(this.scribbleIndex + 1) % this.scribbleDataset.length]

      // Randomize the letters of the current word
      await this.animateRandomizeLetters(from)
      if (from.length < to.length) {
        // Grow from to the length of to
        this.animateGrow(from.length, to.length)
      } else if (from.length > to.length) {
        // Shrink from to the length of to
        this.animateShrink(from.length, to.length)
      }
      // Randomize the letters while revealing the next word
      this.animateUnrandomizeLetters(to)
    },
    async animateRandomizeLetters (str) {
      let strLength = str.length
      let startIndex = 0

      while (strLength > 2) {
        const subsetShown = str.slice(startIndex, startIndex + strLength)
        this.scribbledText = this.randomString(startIndex) + subsetShown + this.randomString(startIndex)
        startIndex++
        strLength -= 2
        await this.wait(150)
      }
      if (strLength === 1) {
        this.scribbledText = this.randomString(str.length)
        await this.wait(150)
      }
    },
    async animateGrow (oldLength, newLength) {
      while (oldLength < newLength - 1) {
        oldLength += 2
        this.scribbledText = this.randomString(oldLength)
        await this.wait(150)
      }
      if (oldLength !== newLength) {
        this.scribbledText = this.randomString(newLength)
        await this.wait(150)
      }
    },
    async animateShrink (oldLength, newLength) {
      while (oldLength > newLength + 1) {
        oldLength -= 2
        this.scribbledText = this.randomString(oldLength)
        await this.wait(150)
      }
      if (oldLength !== newLength) {
        this.scribbledText = this.randomString(newLength)
        await this.wait(150)
      }
    },
    async animateUnrandomizeLetters (str) {
      let strLength = str.length % 2
      let startIndex = Math.floor(str.length / 2)

      if (strLength === 0) {
        strLength = 2
      }

      while (startIndex >= 0) {
        const subsetShown = str.slice(startIndex, startIndex + strLength)
        this.scribbledText = this.randomString(startIndex) + subsetShown + this.randomString(startIndex)
        startIndex--
        strLength += 2
        await this.wait(150)
      }
    },
    randomString (size) {
      let result = ''
      for (let i = 0; i < size; i++) {
        result += String.fromCharCode(Math.floor(Math.random() * 93 + 33))
      }
      return result
    },
    async wait (ms) {
      return new Promise((resolve, reject) => {
        setTimeout(() => resolve(), ms)
      })
    }
  },
  beforeUnmount () {
    clearInterval(this.scribbleInterval)
  },
  created () {
    this.startScribbling()
  }
}
</script>
