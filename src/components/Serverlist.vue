<template>
	<div class="serverlist">
		<ul class="server-list">
      <li class="server-item" :class="item.status" v-for="(item, index) in serverList">
				<img class="face" src="" alt="">
				<div class="cont">
					<p>
						<strong>{{ item.server }}</strong>
						<span>{{ item.status }}</span>
						<span>{{ item.ip }}</span>
						<span>{{ item.path }}</span>
					</p>
					<div class="resource">
						<strong @click="addResource($event, index)">Specif Resource:</strong>
						<ul class="resource-list">
							<li v-for="(resource, i) in item.resources" @click="removeResource(index, i)">{{ resource }}</li>
						</ul>
					</div>
					<a href="" class="btn">Deny</a>
				</div>
			</li>
		</ul>
	</div>
</template>

<style lang="scss" scoped>
  .server-list {
    margin: 0;
    padding: 0;
    list-style: none;
    .server-item {
      position: relative;
      margin: 10px;
      padding: 10px 10px 10px 80px;
      text-align: left;
      border: 1px solid #ccc;
      background-color: #FFFAC6;
      border-radius: 5px;
      .btn {
        position: absolute;
        right: 10px;
        bottom: 10px;
      }
      &.idle {
        background-color: #D3E9C1;
      }
    }
    .face {
      width: 60px;
      height: 60px;
      position: absolute;
      left: 10px;
      top: 50%;
      margin-top: -30px;
      border-radius: 50%;
      background-color: #f3f3f3;
      border: 0;
    }
    .cont {
      p {
        span {
          margin-left: 10px;
          padding-left: 10px;
          border-left: 1px solid #ccc;
        }
      }
    }
  }
  .resource-list {
    display: inline-block;
    list-style: none;
    li {
      display: inline-block;
      margin-left: 10px;
      cursor: pointer;
      &::after {
        content: "X";
        margin-left: 5px;
        padding: 2px 6px;
        border:1px solid #999;
        border-radius: 50%;
      }
      &:hover {
        &::after {
          background-color: #999;
          color: #fff;
        }
      }
    }
  }
  .resource {
    strong {
      cursor: pointer;
    }
  }
</style>

<script>
export default {
  name: 'serverlist',
  props: ['serverList', 'dialogShow'],
  data () {
    return {
    }
  },
  methods: {
    addResource (e, index) {
      console.log(e)
      this.$emit('popup', e, index)
    },
    removeResource (index, i) {
      this.serverList[index].resources.splice(i, 1)
    }
  }
}
</script>