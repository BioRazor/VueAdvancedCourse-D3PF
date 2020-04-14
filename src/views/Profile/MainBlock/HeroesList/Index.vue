<template lang="pug">
    div
        h1 Hero List
        b-table(:items="heroes" :fields="fields" dark hover small striped stacked="sm")
            template(v-slot:cell(name)="data")
                HeroIco(:hero="data.item")
            template(v-slot:cell(class)="data")
                HeroClassLevel(:hero="{ class: data.item.class, level: data.item.level}")
            template(v-slot:cell(kills)="data")
                span {{data.item.kills.elites | formatNumber}}
</template>
<script>
import HeroIco from './HeroIco'
import HeroClassLevel from './HeroClassLevel'
import { formatNumber } from '@/filters/numeral'
export default {
  name: 'HeroesList',
  components: { HeroIco, HeroClassLevel },
  filters: {
    formatNumber
  },
  props: {
    heroes: {
      type: Array,
      required: true
    }
  },
  data () {
    return {
      fields: [
        {
          key: 'name',
          label: 'Name'
        },
        {
          key: 'class',
          label: 'Class',
          sortable: true
        },
        {
          key: 'kills',
          label: 'Elite Kills',
          sortable: true
        }
      ]
    }
  }
}
</script>
