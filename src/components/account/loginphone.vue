<template>
	<div id="tmpl">
		手机:<input type="number" v-model='phone' placeholder="手机">
		短信验证码:<input type="number" v-model='code' placeholder="短信验证码">
		
		<button v-on:click='submit'>登录</button>
		<router-link to="login">
		      <div class="mui-media-body">账号密码登录</div>
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
				this.$http.post('http://www.zfy0351.cn/api/user/login'+"?phone="+this.phone+"&code="+this.code).then(function(res){
					var body = res.body;
					console.log(body)
				})
			}
		}
	}
</script>

<style scoped>
	
</style>