<template lang="pug">
    .top-heroes
        h2.my-4.font-diablo Top Heroes
        b-row
            b-col(sm="4" v-for="hero in heroes" :key="hero.id")
                TopHero(:hero="hero")
</template>
<script>
import TopHero from './TopHero'
export default {
  name: 'TopHeroes',
  components: { TopHero },
  props: {
    heroes: {
      type: Array,
      required: true
    }
  }
}
</script>
