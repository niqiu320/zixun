<template>
	  <body class="body">
	  	<div class="login">
		<h2 class="title">看点资讯精选后台管理系统</h2>
		<el-form ref='userForm' :rules='rules' :model="form" size="mini" label-position="left" >
	    <el-form-item prop='username' label="用户名" label-width="6em">
	      <el-input v-model="form.username"></el-input>
	    </el-form-item>
	    <el-form-item prop='password' label="密码" label-width="6em">
	      <el-input v-model="form.password" type="password"></el-input>
	    </el-form-item>
	  </el-form>
	  <div class="btns">
	  	<el-button size="mini" @click='login'>登录</el-button>
	  </div>
	</div>
   </body>
</template>
<script>
	import axios from '@/http/axios'
	export default {
		data(){
			return {
				form:{},
				rules:{
					username:[{
						required:true,
						message:'请输入用户名',
						trigger:'blur'
					}],
					password:[{
						required:true,
						message:'请输入密码',
						trigger:'blur'
					}]
				}
			}
		},
			methods:{
			login(){
				axios.post('/login',this.form)
				.then((result)=>{
					console.log('success',result);
					this.$root.currentComponent = 'App';
				})
				.catch((error)=>{
					console.log('error',error);
				});
			}
		}
	}
</script>

<style>
    input:-webkit-autofill {
    -webkit-box-shadow: 0 0 0px 1000px white inset !important;
	}
	.body{
		margin: -.5em -.5em;
		position:absolute;
		width:100%;
		height:100%;
		background: url(./assets/beijing.jpg);
	}
	.login {
		width: 400px;
		margin: 0 auto;
       
	}
	.login .title {
		margin-top: 200px;
		text-align: center;
	}
	.login .btns {
		text-align: right;
	}
</style>