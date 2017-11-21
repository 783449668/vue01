<template>
	<div id="tmpl">
		用户名:<input type="text" v-model='username' placeholder="昵称">
		密码:<input type="text" v-model='pwd' placeholder="密码">
		
		<button v-on:click='submit'>登录</button>

		<router-link to="loginphone">
		      <div class="mui-media-body">手机验证码登录</div>
        </router-link>
	</div>
</template>

<script>
	export default{
		data(){
			return{
				username:'',
				phone:'',
				pwd:'',
				code:'',
				key:'',
				source:'',
			}
		},
		methods:{
			submit:function(){
				//console.log(this.username)
				this.$http.post('http://www.zfy0351.cn/api/user/login'+"?username="+this.username+"&password="+this.pwd).then(function(res){
					var body = res.body;
					console.log(body)
				})
			}
		}
	}
</script>

<style scoped>
	
</style>