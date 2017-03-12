<template>
  <header>
    <h1 class="logo">Cruise</h1>
    <navigation></navigation>
  </header>
</template>

<script>
import Navigation from './Navigation'

export default {
  name: 'headerpart',
  components: {
    Navigation
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
header {
  overflow: hidden;
}
header h1 {
  width: 200px;
  float:left;
}
header .nav {
  float: right;
}
</style>
