<template>
	<section class="clearfix">
		<div class="left">
      <add-agent :server-list="serverList" :is-add-agent-show="isAddAgentShow" :dialog-show="isDialogShow"></add-agent>
      <div class="result-list">
        <serverlist :server-list="serverList" :dialog-show="isDialogShow" @popup="showDialog"></serverlist>
        <popupresource v-show="isDialogShow" :is-add-agent-show="isAddAgentShow" :current="currentIndex" :style="popPosition" @addResource="addResource" @close="closePopup"></popupresource>
      </div>
		</div>
		<div class="right">
			<summary-list :summary="summary"></summary-list>
		</div>
	</section>
</template>

<script>
import Serverlist from './Serverlist'
import Popupresource from './Popupresource'
import SummaryList from './SummaryList'
import AddAgent from './AddAgent'

export default {
  name: 'contentPart',
  data () {
    return {
      isDialogShow: false,
      isAddAgentShow: false,
      popPosition: {},
      currentIndex: 0,
      serverList: [
        {
          server: 'ci01.thoughtworks.com',
          status: 'idle',
          ip: '192.168.1.2',
          path: '/server/m1/var/lib/cruise-agent',
          resources: ['ubuntu', 'cent os', 'free BSD']
        },
        {
          server: 'ci02.thoughtworks.com',
          status: 'building',
          ip: '192.168.1.3',
          path: '/server/m2/var/lib/cruise-agent',
          resources: ['Mac os']
        },
        {
          server: 'ci03.thoughtworks.com',
          status: 'building',
          ip: '192.168.142',
          path: '/server/m3/var/lib/cruise-agent',
          resources: ['ubuntu', 'cent os', 'free BSD']
        },
        {
          server: 'ci03.thoughtworks.com',
          status: 'idle',
          ip: '192.168.1.5',
          path: '/server/m4/var/lib/cruise-agent',
          resources: ['Red hat']
        }
      ]
    }
  },
  components: {
    Serverlist,
    Popupresource,
    SummaryList,
    AddAgent
  },
  mounted () {
  },
  computed: {
    summary: function () {
      let arr = {}
      this.serverList.map((k, v) => {
        if (arr[k.status] === undefined) {
          arr[k.status] = 1
        } else {
          arr[k.status] = arr[k.status] + 1
        }
      })
      return arr
    }
  },
  methods: {
    summaryProcess () {
      this.summary = this.serverList.map((e, key) => {
        console.log(e, key)
      })
    },
    showDialog (e, index) {
      console.log(e.target.offsetTop, e.target.clientTop, e.target.offsetParent.offsetTop)
      this.isDialogShow = true
      this.currentIndex = index
      this.popPosition = {
        left: '80px',
        top: (e.target.offsetParent.offsetTop + e.target.offsetTop + 40) + 'px'
      }
    },
    closePopup () {
      this.isDialogShow = false
    },
    addResource (data, index) {
      data.split(',').map((item) => {
        if (item !== '') {
          this.serverList[index].resources.push(item)
        }
      })
      this.closePopup()
    }
  }
}
</script>

<style scoped lang="scss">
section {
	border: 1px solid #ccc;
	position: relative;
  .result-list {
    position: relative;
    z-index: 0;
  }
}
.left {
  position: relative;
	box-sizing: border-box;
	float: left;
	width: 100%;
	padding-right: 260px;
	margin-right: -260px;
  z-index: 1;
}
.right {
	float: right;
	width: 260px;
}

.right::before {
	content: '';
	position: absolute;
	top: 0;
	bottom: 0;
	right: 260px;
	width: 0;
	border-left: 1px solid #ccc;
}
	
</style>