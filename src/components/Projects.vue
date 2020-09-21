<template>
  <div id="projects" class="pt-20 md:pt-8 text-center">
    <h1 class="text-4xl font-bold">Projects</h1>
    <div v-for="(project, idx) in projects" :key="idx" class="text-left mx-8 mb-8">
      <h2 class="block md:inline-block text-xl font-bold">{{project.title}}<span title="Inactive" class="ml-2" v-if="!project.active">✝</span></h2>
      <h3 class="block md:inline-block text-lg md:ml-2 text-gray-600">{{project.secondary}}</h3>
      <ul class="list-disc list-inside">
        <li v-if="project.description">
          <span class="font-light">{{project.description}}</span>
        </li>
        <li v-if="project.role">
          <span class="font-light">Role: {{project.role}}</span>
        </li>
        <li v-if="project.previousTechnologies">
          <span class="font-light">Previous Technologies:<Technology v-for="technology in project.previousTechnologies" :key="technology" :technology="technology" />
          </span>
        </li>
        <li v-if="project.technologies">
          <span class="font-light">Technologies:<Technology v-for="technology in project.technologies" :key="technology" :technology="technology" />
          </span>
        </li>
        <li v-if="project.additionalSkills">
          <span class="font-light">Additional Skills: {{project.additionalSkills}}</span>
        </li>
        <li v-if="project.website">
          <span class="font-light">Website: <a class="underline" :href="project.website" target="_blank">Click Here</a></span>
        </li>
        <li v-if="project.source">
          <span class="font-light">Source Code: <a class="underline" :href="project.source" target="_blank">Click Here</a></span>
        </li>
        <li v-else>
          <span class="font-light">Closed Source</span>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
import Technology from './Technology'

export default {
  name: 'Projects',
  components: {
    Technology
  },
  data () {
    return {
      projects: [
        {
          title: 'Nino',
          secondary: 'Full Stack',
          active: true,
          role: 'Web-Development and Discord Bot Development, Databases, DevOps',
          previousTechnologies: ['Svelte'],
          technologies: ['devicon-typescript-plain', 'devicon-nodejs-plain', 'devicon-vuejs-plain', 'Kotlin', 'devicon-docker-plain', 'devicon-github-plain', 'devicon-redis-plain', 'devicon-mongodb-plain'],
          source: 'https://github.com/NinoDiscord/Nino',
          website: 'https://nino.augu.dev'
        },
        {
          title: 'Bamba in the Magic Kingdom',
          secondary: 'Backend',
          active: true,
          role: 'Backend-Development, Databases',
          technologies: ['devicon-python-plain', 'devicon-postgresql-plain', 'devicon-github-plain'],
          website: 'https://magic-kingdom.live'
        },
        {
          title: 'StaffBot',
          secondary: 'Full Stack',
          role: 'Web-Development and Discord Bot Development, Sysadmin, Databases, DevOps',
          technologies: ['devicon-scala-plain', 'Akka', 'devicon-java-plain', 'devicon-nodejs-plain', 'devicon-react-original', 'devicon-postgresql-plain', 'devicon-docker-plain', 'devicon-github-plain', 'devicon-redis-plain']
        },
        {
          title: 'DonBot',
          secondary: 'Full Stack',
          role: 'Web-Development and Discord Bot Development, Sysadmin, Databases, DevOps',
          technologies: ['devicon-java-plain', 'devicon-nodejs-plain', 'devicon-express-original', 'EJS', 'devicon-postgresql-plain', 'devicon-docker-plain', 'devicon-github-plain', 'devicon-redis-plain'],
          additionalSkills: 'Image Manipulation, External API, Web-Scraping',
          source: 'https://github.com/dondish/OSDonBot'
        },
        {
          title: 'Taki Ai',
          active: true,
          secondary: 'Data Science, Developer',
          description: 'Development of an AI that plays the card game Taki using Deep Q Learning',
          technologies: ['devicon-python-plain', 'TensorFlow, Keras'],
          additionalSkills: 'Hyperparameter tuning, Deep Learning, Reinforcement Learning',
          source: 'https://github.com/dondish/taki-ai'
        },
        {
          title: 'Chordifier',
          active: true,
          secondary: 'Developer',
          description: 'A program and a library that creates, manipulates and plays sound waves',
          technologies: ['devicon-python-plain'],
          additionalSkills: 'Audio Manipulation, Test-Driven Development',
          source: 'https://github.com/dondish/chordifier'
        },
        {
          title: 'Go-Cluster',
          active: true,
          secondary: 'Developer',
          description: 'Go library that assists in creating microservice clusters using TCP and Peer-to Peer connectivity',
          technologies: ['devicon-go-plain', 'Gob format'],
          additionalSkills: 'Networking, Test-Driven Development',
          source: 'https://github.com/dondish/go-cluster'
        },
        {
          title: 'LionPlayer',
          active: true,
          secondary: 'Developer',
          description: 'Go library that can fetch audio tracks from different sources and plays them in Discord',
          technologies: ['devicon-go-plain'],
          additionalSkills: 'Audio Manipulation, Web Scraping, Test-Driven Development',
          source: 'https://github.com/dondish/lionplayer'
        }
      ]
    }
  }
}
</script>
