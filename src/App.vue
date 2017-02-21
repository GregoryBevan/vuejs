<template>
  <nav-bar></nav-bar>
</template>

<script>
import NavBar from './navbar/NavBar.vue'

export default {
  name: 'app',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App'
    }
  },
  components: {
    NavBar
  }
}
</script>

<style lang="scss">
  @import './assets/scss/style.scss';
</style>
