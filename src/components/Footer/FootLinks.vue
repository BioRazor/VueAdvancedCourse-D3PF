<template lang="pug">
    b-nav(small align="start")
        b-nav-item(:to="{name: 'Home'}") Home
        b-nav-item(:to="{name: 'About'}") About
        b-nav-item(href="https://github.com/baumannzone/diablo3-vue-platzi" target="_blank") Github
</template>

<script>
export default {
  name: 'FootLinks'
}
</script>
