<template>
  <div id="app">
    <img
      class="img-fluid"
      alt="Hotels logo"
      src="./assets/logo.png"
      width="70%"
      styles="text-align: center;">
    <HotelsForm
      title="Registration"
      action="Save"/>
  </div>
</template>

<script>
import HotelsForm from './components/Hotels/Form.vue'

export default {
  name: 'app',
  components: {
    HotelsForm
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
