<template lang="pug">
    .multi-stats.pl-jg-4
        hr.bg-white.mt-5.d-lg-none
        h2.font-diablo.my-4S Stats
        .stats.d-flex.flex-column.bg-dark.p-3
            SingleStat(
                class="mb-3"
                ico-name="skull"
                ico-color="#9E9E9E"
                :info="{value: stats.kills.monsters, text: 'Lifetime Kills'}"
            )
            SingleStat(
                class="mb-3"
                ico-name="crown"
                ico-color="#ffc107"
                :info="{value: stats.kills.elites, text: 'Elite Kills'}"
            )
            SingleStat(
                class="mb-3"
                ico-name="dungeon"
                ico-color="#795548"
                :info="{value: stats.paragonLevel, text: 'Paragon Level'}"
            )
            TimePlayed(:timePlayed="timePlayed")
</template>
<script>
import heroName from '@/mixins/heroName'
import SingleStat from './SingleStat'
import TimePlayed from './TimePlayed'
import { HeroData } from '@/utils/typeValidation.js'
export default {
  name: 'PlayerStats',
  mixins: [heroName],
  components: {
    TimePlayed,
    SingleStat
  },
  props: {
    stats: {
      type: Object,
      required: true
    }
  },
  computed: {
    timePlayed () {
      return Object.keys(this.stats.timePlayed)
        .sort()
        .map(hero => {
          return new HeroData(
            this.classToName(hero),
            this.stats.timePlayed[hero],
            hero
          )
        })
    }
  }
}
</script>
