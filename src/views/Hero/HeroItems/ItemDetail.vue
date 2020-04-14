<template lang="pug">
    .text-center.bg-dark.h-100.pt-3.d3-icon-item(:class="itemClassColor")
        .d-flex.flex-column.justify-content-between.h-100
            template(v-if="item.id")
                div
                    div(v-if="item" class="item-image" v-b-tooltip.hover :title="item.flavorText")
                        p.text-muted {{ item.name }}
                        img(:src="itemUrl" :alt="item.slotName + ' ' + item.name ")
                div
                    template(v-if="itemHasGems")
                        small {{ gemOrJewel }}:
                        ul.list-inline
                            li(v-for="(gem, index) in item.gems" :key="'gem-'+index" class="list-inline-item")
                                ItemDetailGem(:gem="gem" v-b-tooltip.hover :title="gem.attributes")
            p(v-else)
                b-badge.text-dark {{ item.slotName }}
</template>
<script>
import ItemDetailGem from './ItemDetailGem'
export default {
  name: 'ItemDetail',
  components: { ItemDetailGem },
  props: {
    item: {
      type: Object || undefined,
      required: true
    }
  },
  computed: {
    // Resuelve la URL de la imagen
    itemUrl () {
      const host = 'http://media.blizzard.com/d3/icons/items/large/'
      return `${host}${this.item.icon}.png`
    },
    // Comprueba si el item tiene gemas
    itemHasGems () {
      return Object.prototype.hasOwnProperty.call(this.item, 'gems')
    },
    // Si tiene gemas, comprueba si es Gema o Joya
    // Puede haber varias Gemas. Solo puede haber una Joya. No puede haber joyas y gemas mezcladas
    gemOrJewel () {
      return this.item.gems[0].isGem ? 'Gems' : 'Jewel'
    },
    // Clase CSS para saber la rareza
    itemClassColor () {
      if (Object.prototype.hasOwnProperty.call(this.item, 'displayColor')) {
        return `item-${this.item.displayColor}`
      }
      // Si no tiene color (es que no hay objeto equipado)
      return 'item-none'
    }
  }
}
</script>

<style lang="stylus">
.d3-icon-item
    min-height 100px
    // El borde de la caja va determinar la rareza del objeto, segun el color que tenga
    border-top-style solid
    border-top-width 4px

    &.item-none
        border-color transparent

    &.item-green
        border-color #8bc34a

    &.item-orange
        border-color #ff9800

    &.item-yellow
        border-color #ffeb3b

    &.item-blue
        border-color #03a9f4

    &.item-white
        border-color #a0aab5
</style>
