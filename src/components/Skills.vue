<template>
  <div id="skills" class="pt-20 md:pt-8 text-center">
    <h1 class="text-4xl mb-8 font-bold">Skills</h1>
    <div id="Proficiency" class="text-left mx-8 mb-8">
        <h2 class="texl-l md:text-xl font-bold">Proficiency in Programming Languages and Tools</h2>
        <ul class="list-disc list-inside">
          <li class="font-light break-all">Programming Languages:<Technology v-for="technology of programmingLanguages" :key="technology" :technology="technology" /></li>
          <li class="font-light break-all">Environments:<Technology v-for="technology of environments" :key="technology" :technology="technology" /></li>
          <li class="font-light break-all">Databases:<Technology v-for="technology of databases" :key="technology" :technology="technology" /></li>
          <li class="font-light break-all">DevOps:<Technology v-for="technology of devops" :key="technology" :technology="technology" /></li>
          <li class="font-light break-all">Frameworks:<Technology v-for="technology of frameworks" :key="technology" :technology="technology" /></li>
        </ul>
        <h2 class="texl-l md:text-xl mt-8 font-bold">Leadership and Teamwork</h2>
        <ul class="list-disc list-inside">
          <li class="font-light">As a member of the Odyssey Program, I worked on projects as a member and a leader of my team under close deadlines.</li>
          <li class="font-light">As a leader and a member of Hackathon teams.</li>
        </ul>
    </div>
  </div>
</template>

<script>
import Technology from './Technology'

export default {
  name: 'Skills',
  components: {
    Technology
  },
  data () {
    return {
      programmingLanguages: ['devicon-c-plain', 'devicon-cplusplus-plain', 'devicon-rust-plain', 'devicon-python-plain', 'devicon-scala-plain', 'Kotlin', 'devicon-javascript-plain', 'devicon-typescript-plain', 'devicon-java-plain', 'devicon-csharp-plain', 'FSharp', 'devicon-go-plain', 'D', 'devicon-html5-plain', 'devicon-css3-plain'],
      environments: ['devicon-intellij-plain', '(And other Jetbrains IDEs)', 'devicon-visualstudio-plain'],
      databases: ['devicon-postgresql-plain', 'devicon-mysql-plain', 'MariaDB', 'devicon-redis-plain', 'devicon-mongodb-plain', 'Cassandra'],
      devops: ['devicon-docker-plain', 'Kubernetes', 'devicon-travis-plain', 'devicon-github-plain', 'devicon-git-plain', 'PM2'],
      frameworks: ['devicon-nodejs-plain', 'devicon-react-original', 'devicon-vuejs-plain', 'Svelte, Akka, Project Reactor, WinForms, Flask, Tensorflow, NumPy, SciPy']
    }
  }
}
</script>
