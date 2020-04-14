<template lang="pug">
  .container
    HeaderBar
    router-view
    FooterBar
</template>
<script>
import HeaderBar from '@/components/HeaderBar/Index'
import FooterBar from '@/components/Footer/Index'
export default {
  name: 'MainLayout',
  components: {
    HeaderBar,
    FooterBar
  }
}
</script>
