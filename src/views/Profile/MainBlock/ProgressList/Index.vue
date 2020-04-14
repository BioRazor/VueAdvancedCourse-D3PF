<template lang="pug">
    .progression-bosses.pt-4.mt-.border-top
        h2.font-diablo.mb-4 Progression
        b-row
            b-col(v-for="(val, key) in sortedActs" :key="key" class="col-12 col-md-2")
                .bg-dark.rounded.mb-2
                    ProgressItem(:act="{actNum: key, value: val}")
</template>
<script>
import ProgressItem from './ProgressItem'
export default {
  name: 'ProgressBosses',
  components: {
    ProgressItem
  },
  props: {
    acts: {
      type: Object,
      required: true
    }
  },
  computed: {
    sortedActs () {
      return Object.keys(this.acts)
        .sort()
        .reduce((a, c) => {
          a[c] = this.acts[c]
          return a
        }, {})
    }
  }
}
</script>
<style lang="stylus">
  .progression-bosses
    .boss-img
      display block

      .act
        margin 0 auto
        width 50px
        height 55px
</style>
