<template>
	<div class="reg">
		<div class="regHead">
			<router-link to="/Use/Login">
				<span class="HeadIcon">
					<img src="../../../../static/img/left-arrow.png"/>
				</span>
			</router-link>
			<span class="HeadTitle">注册</span>
		</div>
		<div class="regContent">
			<p class="title-p">这是一个神秘的后花园，里面有无尽的财富和宝藏等着你去发现，现在就注册账号开启你的美丽探索之旅吧！</p>
			<div class="error-msg"></div>
			<form action="" method="get" id="regForm">
				<p>
					<input type="text" id="regVal" value="" v-model="regZh" placeholder="请输入11位手机号" @blur="regUse" />
					<input type="password" name="" v-model="regMm" placeholder="请输入6位以上密码" id="regPass" @blur="regPass" />
				</p>
				<!--<router-link to="/Use/Login">-->
					<input type="submit" value="注册" id="regBtn" @click="regBtn" />
				<!--</router-link>-->
				
			</form>
		</div>
	</div>
</template>

<script>
	export default{
		name:"Reg",
		components:{},
		data(){
			return{
				name:'我是Reg',
				regZh:'',
				regMm:'',
				regUsername:false,
				regPassword:false,
				
			}
		},
		methods:{
			regUse(){
				var regPhone = /^1[3456789]\d{9}$/;
				console.log(this.regZh)
				if(regPhone.test(this.regZh)){
					console.log('手机号验证成功');
					this.regUsername = true;
				}else{
					console.log('手机号验证失败')
				}
			},
			regPass(){
				console.log(this.regMm)
				if(this.regMm.length >= 6){
					console.log('密码验证成功')
					this.regPassword = true;
				}else{
					console.log('密码长度为6位以上')
				}
			},
			regBtn(){
				if(this.regUsername == true && this.regPassword == true){
					console.log(this.regUsername)
					console.log(this.regPassword)
					window.localStorage.setItem('regZh',this.regZh);
					window.localStorage.setItem('regMm',this.regMm);
					this.$router.push({path:'/Use/Login'})
				}
			}

			
		}
	}
</script>

<style lang="less" scoped="scoped">
@import url("../../../styles/main.less");
.reg{
	.regHead{
		width:100%;
		.h(45);
		border-bottom: 1px solid #E2E2E2;
    	color: #535353;
		position:fixed;
		top:0;
		.fs(14);
		background:#fff;
		/*z-index:1;*/
			.HeadIcon{
				display: inline-block;
				width: 45px;
				height:70%;
				margin-top: 11px;
				padding-left: 15px;
				position: absolute;
				left: 0;
				img{
					width:22px;
				}
			}
			.HeadTitle{
				display: block;
				text-align:center;
				.fs(18);
				.lh(45);
			}
	}
	.regContent{
		margin: 0px 3%;
   		margin-top: 54px;
		.title-p{
			color: #555555;
    		font-size: 14px;
    		margin: 10px 0px;
		}
		#regForm{
			p{
				.fs(14);
				border: 1px solid #e2e2e2;
				input{
					width: 100%;
					.h(38);
					.fs(14);
					border: none;
    				padding: 1px 2%;
    				outline: none;
				}
				input+input{
					border-top: 1px solid #e2e2e2;
				}
				
			}
			
				#regBtn{
					width: 100%;
					.h(38);
					margin-top: 10px;
					background-color: #ff498c;
					color: #fff;
					font-size: 14px;
				    text-align: center;
				    line-height: 36px;
				    margin: 10px 0px 5px;
				    border: 1px solid #ff498c;
				    border-radius: 3px;
					
				}
			
			
		}
	}
}
</style>