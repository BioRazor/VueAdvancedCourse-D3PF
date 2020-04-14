<template lang="pug">
    section.hero-items.mb-5
        h2.font-diablo Items
        hr.bg-white
        b-row
            b-col(cols="4" offset="4")
                ItemDetail(:item="itemsData.head")
        hr
        b-row
            b-col
                ItemDetail(:item="itemsData.shoulders")
            b-col
                ItemDetail(:item="itemsData.torso")
            b-col
                ItemDetail(:item="itemsData.neck")
        hr
        b-row
            b-col
                ItemDetail(:item="itemsData.hands")
            b-col
                ItemDetail(:item="itemsData.waist")
            b-col
                ItemDetail(:item="itemsData.bracers")
        hr
        b-row
            b-col
                ItemDetail(:item="itemsData.leftFinger")
            b-col
                ItemDetail(:item="itemsData.legs")
            b-col
                ItemDetail(:item="itemsData.rightFinger")
        hr
        b-row
            b-col
                ItemDetail(:item="itemsData.mainHand")
            b-col
                ItemDetail(:item="itemsData.feet")
            b-col
                ItemDetail(:item="itemsData.offHand")
</template>
<script>
import ItemDetail from './ItemDetail'

// Objeto con las keys de los 'items' del personaje
const defaultItems = {
  head: {
    slotName: 'head'
  },
  shoulders: {
    slotName: 'Shoulders'
  },
  torso: {
    slotName: 'Torso'
  },
  neck: {
    slotName: 'Neck'
  },
  hands: {
    slotName: 'Hands'
  },
  waist: {
    slotName: 'Waist'
  },
  bracers: {
    slotName: 'Bracers'
  },
  leftFinger: {
    slotName: 'Left Finger'
  },
  legs: {
    slotName: 'Legs'
  },
  rightFinger: {
    slotName: 'Right Finger'
  },
  mainHand: {
    slotName: 'Main Hand'
  },
  feet: {
    slotName: 'Feet'
  },
  offHand: {
    slotName: 'Off Hand'
  }
}

export default {
  name: 'HeroItems',
  components: { ItemDetail },
  props: {
    items: {
      type: Object,
      required: true
    }
  },
  computed: {
    itemsData () {
      // Fusionar objetos:
      // Esto lo hacemos para mostrar el hueco vacío en caso de que ese objeto no esté equipado
      // Si NO hay item equipado, manda el valor de 'defaultItems' correspondiente
      // Si hay item equipado, manda la info del item
      return {
        ...defaultItems,
        ...this.items
      }
    }
  }
}
</script>
