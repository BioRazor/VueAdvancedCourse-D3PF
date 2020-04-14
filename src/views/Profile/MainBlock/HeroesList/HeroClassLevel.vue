<template lang="pug">
    .hero-name-level
        span {{ classToName(hero.class) }}
        span ·
        span.text-monospace.font-weight-bold {{ hero.level }}
</template>
<script>
// Traemos el mixin
import heroName from '@/mixins/heroName.js'

export default {
  name: 'HeroNameLevel',
  // Lo damos de alta
  mixins: [heroName],
  props: {
    hero: {
      required: true,
      type: Object
    }
  }
}
</script>
