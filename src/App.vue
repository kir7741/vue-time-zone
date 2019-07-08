<template>
  <div id="app">
    <TimeZone/>
  </div>
</template>

<script>
import TimeZone from './components/TimeZone.vue'

export default {
  name: 'app',
  components: {
    TimeZone
  }
}
</script>

<style lang="scss">
@import './scss/_mixin.scss';
#app {
  font-family: 'Open Sans', 'Avenir', Helvetica;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
body {
  margin: 0;
  height: 100vh;
  min-height: 800px;
  background-color: $primaryBgColor;
}
</style>
