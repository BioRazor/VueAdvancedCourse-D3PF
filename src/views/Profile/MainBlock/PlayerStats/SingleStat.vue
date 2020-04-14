<template lang="pug">
    .single-stat.w-100
        b-card.text-body
            .d-flex
                .d-block.ico-cont
                    .text-center
                        font-awesome-icon(
                            :icon="icoName"
                            class="fa-3x"
                            :style="{color: icoColor}"
                        )
                .flex-grow-1
                    h4.font-weight-bold.mb-0 {{ info.value | formatNumber }}
                    span.text-muted.font-weight-light.mb-0 {{ info.text }}
</template>
<script>
import { formatNumber } from '@/filters/numeral'

export default {
  name: 'SingleStat',
  filters: {
    formatNumber
  },
  props: {
    icoName: {
      required: true,
      type: String
    },
    icoColor: {
      required: true,
      type: String
    },
    info: {
      required: true,
      type: Object
    }
  }
}
</script>

<style lang="stylus" scoped>
  .single-stat
  .ico-cont
      width 80px
</style>
