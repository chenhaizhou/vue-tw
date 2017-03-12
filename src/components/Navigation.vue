<template>
	<div class="nav">
		<ul class="nav-list">
			<li><a href="">List</a></li>
			<li><a href="">Server</a></li>
			<li><a href="">Ci</a></li>
			<li><a class="">{{ item }}</a></li>
		</ul>
	</div>
</template>

<script>
export default {
  name: 'nav',
  data () {
    return {
      item: 'About'
    }
  }
}
</script>

<style scoped>
h1, h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>