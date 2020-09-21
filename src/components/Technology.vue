<template>
    <span class="ml-2">
        <i :title="extractTitle(technology)" v-if="technology.startsWith('devicon')" :class="technology"></i><span v-else>{{technology}}</span>
    </span>
</template>

<script>
export default {
  props: ['technology'],
  methods: {
    extractTitle (technologyName) {
      return this.capitalize(technologyName.split('-')[1])
    },
    capitalize (str) {
      return str[0].toUpperCase() + str.slice(1).toLowerCase()
    }
  }
}
</script>
