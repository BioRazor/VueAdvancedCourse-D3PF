<template lang="pug">
  .home-view
    HomeTitle
    MainForm
</template>

<script>
import HomeTitle from './HomeTitle'
import MainForm from './HomeForm'
export default {
  name: 'Home',
  components: {
    HomeTitle,
    MainForm
  }
}
</script>
