<template>
  <div id="content">
    <nav-bar></nav-bar>
    <form-component></form-component>
  </div>
</template>

<script>
import NavBar from './navbar/NavBar.vue'
import FormComponent from './form/FormComponent.vue'

export default {
  name: 'app',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App'
    }
  },
  components: {
    NavBar,
    FormComponent
  }
}
</script>

<style lang="scss">
  @import './assets/scss/style.scss';
</style>
