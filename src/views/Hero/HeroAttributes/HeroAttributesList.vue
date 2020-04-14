<template lang="pug">
    ul.list-unstyled
        li.mb-1(v-for="attr in attributes" :key="attr.name")
            .d-flex.justify-content-between
                .pl-2.text-capitalize.name-text {{ attr.name }}
                .px-2.text-monospace {{ attr.val | formatNumber }}
</template>
<script>
import { formatNumber } from '@/filters/numeral'

export default {
  name: 'AttributeList',
  filters: { formatNumber },
  props: {
    attributes: {
      type: Array,
      required: true
    }
  }
}
</script>

<style lang="stylus">
    ul
        li
            .name-text
                color #efb45d
                font-weight 600
</style>
