<template lang="pug">
    .header-bar
        .navigation-bar
          b-navbar(toggleable="lg" type="dark" variant="dark")
            b-navbar-brand(:to="{name: 'Home'}")
              img(src="@/assets/img/diablo-iii.svg" alt="D3" width="30")
              span.font-diablo.ml-2 {{ title }}
</template>
<script>
export default {
  name: 'HeaderBar',
  data () {
    return {
      title: process.env.VUE_APP_TITLE
    }
  }
}
</script>
