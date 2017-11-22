<!-- 以后项目的根组件 -->
<template>
	<div>
		<!-- 1.0.1 统一的返回功能 -->
		<div  v-if="isshow" id="back">
			<a href="javascript:void(0)" @click="backto">返回</a>
		</div>
		<!-- 1.0 利用mint-ui中的header组件四线整个系统的头部 -->
		<header>
			<div v-if="ishidden" id="indexheard">
				<span class="icon01">
					<img src="../statics/imgs/icon01.png">
					<input type="text" placeholder="请输入..." id="search">
				</span>
			
			
				<span class="icon02"><img src="../statics/imgs/icon02.png"></span>
			</div>
		</header>
		
		<!-- 2.0 利用vue-route的<router-view>进行占位 -->
		<router-view>
			
		</router-view>
		<!-- 3.0 利用mui中的tabbar组件实现系统的地步 -->
		<nav class="mui-bar mui-bar-tab">
			<router-link class="mui-tab-item" to="/">
				<span class="mui-icon">
					<img src="../statics/imgs/iconhome.png">
				</span>
				<span class="mui-tab-label">首页</span>
			</router-link>
			<router-link class="mui-tab-item" to="/mission/mission">
				<span class="mui-icon">
					<span class="mui-badge">0</span>
					<img src="../statics/imgs/icon03.png">
				</span>
				<span class="mui-tab-label">任务大厅</span>
			</router-link>
			<router-link class="mui-tab-item" id="zhuye" to="/">
					
					<span class="mui-icon" id="money" >
						<img src="../statics/imgs/zhuye_35.png">
					</span>
					
			</router-link>
			<router-link class="mui-tab-item" to="/shopcar">
				<span class="mui-icon">
					
					<img src="../statics/imgs/icon05.png">
				</span>
				<span class="mui-tab-label">信息中心</span>
			</router-link>
			<router-link class="mui-tab-item" to="/set">
				<span class="mui-icon">
					<img src="../statics/imgs/iconuser.png">
				</span>
				<span class="mui-tab-label">个人中心</span>
			</router-link>
		</nav>
	

	
	</div>
</template>

<script>
	export default{  // es6的导出对象的写法
		data(){  //等价于 es5的 data:function(){
			return {
				isshow:false,
				ishidden:true
			}
		},
		watch:{
			//检测路由变化 实现返回首页后 back隐藏
			'$route':function(newroute,oldroute){
				//console.log(newroute,oldroute)
				if(newroute.path.toLowerCase() == '/'){
					this.isshow = false;
					this.ishidden = true;
				}else{
					this.isshow = true;
					this.ishidden = false;
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
		top: 13px;
		left: 13px;
		z-index: 101;
	}
	#back a{
		color: white;
		font-size: 16px;
	}
	header{
		width: 100%; 
		height: 50px;
		background-color: #4171AE;
	}
	header .icon01{
		position: absolute;
		display: block;
		width: 70%;
		height: 35px;
		z-index: 101;
		left:15%;
	}
	header .icon01 img{
		position: absolute;
		width: 25px;
		height: 25px;
		top:12px;
		left: 10px;
		z-index: 1011;
	}

	header .icon02{
		position: absolute;
		display: block;
		width: 35px;
		height: 35px;
		z-index: 101;
		top:10px;
		right: 10px;
	}
	header .icon02 img{
		width: 30px;
		height: 28px;
	}
	#search{
		position: absolute;
		width:100%;
		height: 30px;
		background-color: #275491;
		border-radius: 20px;
		font-size: 16px;
		padding-left: 40px;
		top: 10px;
		color: #8B9DBC;
	}
	#zhuye img{
		width: 80%;
	}
	.mui-bar{
		height: 60px;
		padding-bottom: 5px;
	}
	#money{
		width: 50px;
		height: 50px;
		background-color: #08306E;
		border-radius: 25px;
	}
	.mui-icon img{
		width: 100%;
		margin-top: 4px;
	}

</style>