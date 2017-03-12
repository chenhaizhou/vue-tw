<template>
	<div class="popup">
		<input type="text" placeholder="eg: aaa, bbb" v-model="resources">
		<input type="button" value="Add Resource" @click="addResources(current)">
		<input type="button" value="Cancel" @click="closePopup">
	</div>
</template>

<style lang="scss">
	.popup {
		position: absolute;
		width: 60%;
		padding: 15px;
		border:1px solid #999;
		border-radius: 10px;
		background-color: #D3E9C1;
		text-align: left;
		&::before, &::after {
			content: '';
			display: block;
			width: 0;
			height: 0;
			position: absolute;
			top: -20px;
			left: 40px;
			border-width: 0 20px 20px 20px;
			border-style: solid;
			border-color: transparent transparent #d3e9c1;
			z-index: 1;
		}
		&::after {
			top: -21px;
			z-index: 0;
			border-color: transparent transparent #999;
		}
		input[type='text']{
			display: block;
			height: 20px;
			width: 100%;
			margin-bottom: 10px;
			line-height: 20px;
			border: 1px solid #ccc;
		}
	}
</style>

<script>
  export default {
    name: 'popupResource',
    props: ['current'],
    data () {
      return {
        resources: ''
      }
    },
    methods: {
      closePopup () {
        this.isShowDialog = false
        this.$emit('close')
      },
      addResources (index) {
        this.$emit('addResource', this.resources, index)
        this.resources = ''
      }
    }
  }
</script>