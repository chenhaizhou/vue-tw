<template>
  <div id="app">
    <img src="./assets/logo.png" class="logo">
    <headerpart></headerpart>
    <contentPart />
    <hello></hello>
  </div>
</template>

<script>
import Hello from './components/Hello'
import Headerpart from './components/Headerpart'
import ContentPart from './components/ContentPart'

export default {
  name: 'app',
  components: {
    Headerpart,
    ContentPart,
    Hello
  }
}
</script>

<style scope>
.logo {
  max-height: 100px;
}
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  font-size: 1.2rem;
}
</style>
