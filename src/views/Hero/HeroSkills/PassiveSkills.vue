<template lang="pug">
    .passive-skills
        h4.my-5 Passive
            b-row
                b-col(v-for="(skill, idx) in skills" :key="idx" cols="6" lg="12")
                    PassiveSkill(:skill="skill.skill")
</template>
<script>
import PassiveSkill from './PassiveSkill'

export default {
  name: 'PassiveSkills',
  components: { PassiveSkill },
  props: {
    skills: {
      type: Array,
      required: true
    }
  }
}
</script>
