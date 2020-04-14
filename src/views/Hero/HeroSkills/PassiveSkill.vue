<template lang="pug">
    .d-flex.align-items-center.mb-3(v-b-tooltip.hover :title="skill.description")
        .mr-2
            img(:src="skillUrl")
        div
            p.skill-name.m-0 {{ skill.name }}
</template>
<script>
export default {
  name: 'PassiveSkill',
  props: {
    skill: {
      required: true,
      type: Object
    }
  },
  computed: {
    skillUrl () {
      const sizes = {
        21: 21,
        42: 42,
        64: 64
      }
      const host = `http://media.blizzard.com/d3/icons/skills/${sizes[42]}/`
      return `${host}${this.skill.icon}.png`
    }
  }
}
</script>
