<!-- 以后项目的根组件 -->
<template>
	<div>
		<!-- 1.0.1 统一的返回功能 -->
		<div  v-if="isshow" id="back">
			<a href="javascript:void(0)" @click="backto">返回</a>
		</div>
		<!-- 1.0 利用mint-ui中的header组件四线整个系统的头部 -->
		<mt-header fixed title="Vue项目"></mt-header>
		<!-- 2.0 利用vue-route的<router-view>进行占位 -->
		<router-view>
			
		</router-view>
		<!-- 3.0 利用mui中的tabbar组件实现系统的地步 -->
		<nav class="mui-bar mui-bar-tab">
			<router-link class="mui-tab-item" to="/">
				<span class="mui-icon mui-icon-home"></span>
				<span class="mui-tab-label">首页</span>
			</router-link>
			<router-link class="mui-tab-item" to="/tabbar-with-chat">
				<span class="mui-icon mui-icon-email"></span>
				<span class="mui-tab-label">消息</span>
			</router-link>
			<router-link class="mui-tab-item" to="/shopcar">
				<span class="mui-icon mui-icon-contact"><span class="mui-badge">0</span></span>
				<span class="mui-tab-label">购物车</span>
			</router-link>
			<router-link class="mui-tab-item" to="/set">
				<span class="mui-icon mui-icon-gear"></span>
				<span class="mui-tab-label">设置</span>
			</router-link>
		</nav>
	

	
	</div>
</template>

<script>
	export default{  // es6的导出对象的写法
		data(){  //等价于 es5的 data:function(){
			return {
				isshow:false
			}
		},
		watch:{
			//检测路由变化 实现返回首页后 back隐藏
			'$route':function(newroute,oldroute){
				//console.log(newroute,oldroute)
				if(newroute.path.toLowerCase() == '/'){
					this.isshow = false;
				}else{
					this.isshow = true;
				}
			}
		},
		methods:{
			backto(){
				//利用路由对象中go（-1）实现
				this.$router.go(-1);
			}
		},
		created(){

		}
	}
</script>

<style scoped>
/*当前页面的css样式写到这里，其中scoped表示这个里面写的css代码只是在当前组件页面上有效，不会去影响到其他组件页面*/
	#back{
		width: 60px;
		position: absolute;
		top: 10px;
		left: 10px;
		z-index: 101;
	}
	#back a{
		color: white;
		font-size: 16px;
		font-weight: bold;
	}
</style>