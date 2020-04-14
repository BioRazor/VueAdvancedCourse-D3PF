<template lang="pug">
    .d-flex.align-items-center.mb-3
        .mr-2
            span.slot(:class="slotClass")
            img(:src="skillUrl")
        div
            p.skill-name.m-0(v-b-tooltip.hover :title="skill.description")
                |{{ skill.name }}
            small.rune-name.text-muted(v-if="rune" v-b-tooltip.hover :title="rune.description")
                |{{ rune.name }}
</template>
<script>
export default {
  name: 'ActiveSkill',
  props: {
    skill: {
      required: true,
      type: Object
    },
    rune: {
      required: false,
      type: Object
    },
    slotNum: {
      required: true,
      type: Number || String
    }
  },
  computed: {
    skillUrl () {
      // Posibles tamaños (px)
      const sizes = [21, 42, 64]
      // API URL para imágenes
      const host = `http://media.blizzard.com/d3/icons/skills/${sizes[1]}/`
      // Ejemplo:
      // http://media.blizzard.com/d3/icons/skills/42/p6_necro_bonespikes.png
      return `${host}${this.skill.icon}.png`
    },
    // Clase CSS para los slots
    slotClass () {
      return `slot-${this.slotNum}`
    }
  }
}
</script>
