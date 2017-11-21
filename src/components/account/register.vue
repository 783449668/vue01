<template>
	<div id="tmpl">
		昵称:<input type="text" v-model='username' placeholder="昵称">
		手机:<input type="number" v-model='phone' placeholder="手机">
		密码:<input type="text" v-model='pwd' placeholder="密码">
		短信验证码:<input type="number" v-model='code' placeholder="短信验证码">
		激活码:<input type="text" v-model='key' placeholder="激活码">
		手机/pc:<input type="number" v-model='source' placeholder="1或者2">
		<button v-on:click='submit'>注册</button>
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
				this.$http.post('http://www.zfy0351.cn/api/user/register'+"?username="+this.username+"&phone="+this.phone+"&password="+this.pwd+"&code="+this.code+"&promote_code="+this.key+"&source="+this.source).then(function(res){
					var body = res.body;
					if(body.code == 1000){
						alert("注册成功，请立即激活！")
					}else if(body.code ==2000 ){
						alert("注册成功")
					}
					alert("注册失败")
				})
			}
		}
	}
</script>

<style scoped>
	
</style>