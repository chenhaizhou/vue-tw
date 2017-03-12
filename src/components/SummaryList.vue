<template>
	<div class="summary-box">
		<h3>Summary</h3>
		<ul class="summary-list">
			<li v-for="(v, k) in summary">
				<strong>{{ k }}</strong>
				<span>{{ v }}</span>
			</li>
		</ul>
	</div>
</template>
<script>
export default {
  props: ['summary'],
  data () {
    return {}
  }
}
</script>
<style lang="scss">
	.summary-list {
    li {
      text-align: left;
      font-size: 0;
      strong ,span {
        display: inline-block;
        width: 50%;
        font-size: 1.2rem;
      }
    }
  }
</style>