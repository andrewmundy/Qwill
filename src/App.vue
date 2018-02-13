<template>
  <div id="app">
    <router-view v-bind="{
      toggle,
    }"/>
  </div>
</template>

<script>

export default {
  name: 'app',
  data () {
    return {
    }
  }
}
</script>
<style lang="scss">
  @import './assets/main.scss';
   #app {
    //  background:black;
     font-family: $sans-serif;
     -webkit-font-smoothing: antialiased;
     -moz-osx-font-smoothing: grayscale;
     text-align: center;
     padding: 0px;
    //  height: 100vh;
    //  background-size: cover;
 }
</style>
