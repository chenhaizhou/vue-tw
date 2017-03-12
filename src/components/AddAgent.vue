<template>
	<div class="add-agent-wrap">
		<span class="btn" @click="showPopup">+ Add agent</span>
		<div class="popup" v-show="isAddAgentShow">
      <label>Name</label>
			<input type="text" placeholder="eg: agentName1" v-model="agentName">
      <label>IP</label>
      <input type="text" placeholder="eg: 192.168.1.2" v-model="agentIp">
			<input type="button" value="Add Agent" @click="addAgent">
			<input type="button" value="Cancel" @click="closePopup">
		</div>
	</div>
</template>

<script>
  export default {
    name: 'addAgent',
    props: ['serverList', 'isAddAgentShow', 'dialogShow'],
    data () {
      return {
        agentName: '',
        agentIp: '',
        agentStatus: 'idle'
      }
    },
    methods: {
      showPopup () {
        this.isAddAgentShow = !this.isAddAgentShow
        if (this.dialogShow) {
          this.dialogShow = false
        }
      },
      closePopup () {
        this.isAddAgentShow = false
        this.agentName = ''
        this.agentIp = ''
      },
      addAgent () {
        this.serverList.push({
          server: this.agentName,
          status: this.agentStatus,
          ip: this.agentIp,
          path: '/server/m' + (this.serverList.length + 1) + '/var/lib/cruise-agent',
          resources: []
        })
        this.closePopup()
      }
    }
  }
</script>

<style lang="scss" scoped>
	.add-agent-wrap {
    position: relative;
    margin: 20px 20px 10px;
    text-align: right;
    z-index: 1;
    span {
      cursor: pointer;
    }
  }
  .popup {
    position: absolute;
    left: auto;
    right: -20px;
    top: 40px;
    &::before, &::after {
      left: auto;
      right: 40px;
    }
  }
</style>