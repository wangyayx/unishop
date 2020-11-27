<template>
	<view class="login">
		<view class="box">
			<view class="from">
				<view class="row">
					<input type="text" name="mobile">
					<i class="iconfont icon-erji-yonghuguanli"></i>
				</view>
				<view class="row">
					<input type="password" name="pwd">
					<i class="iconfont icon-icon-"></i>
					<text class="forgetPassword" @tap="goforgetPassword">忘记密码</text>
				</view>
				<view class="loginCheckText"></view>
				<view class="row">
					<button class="btn" type="default">登录</button>
				</view>
			</view>				
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				
			}
		},
		methods: {
			goforgetPassword(){
				uni.navigateTo({
					url:"/pages/login/forgetPassword"
				})
			},
		}
	}
</script>

<style>
	page{
		height: 100%;
	}
.login{
	width: 100%;
	height: 100%;
	background: url(/static/login_bg.jpg) no-repeat center center;
	background-size: cover;
}
.login .box{
	width: 100%;
	background-size: cover;
	position: absolute;
	bottom: 0px;
	left: 0;
}
.login .box .from{
	width: 70%;
	position: absolute;
	bottom: 180px;
	left: 50%;
	margin-left: -35%;
}
.login .row{
	padding: 10px 0;
	text-align: center;
	position: relative;
}
.login .loginCheckText{
	text-align: center;
	font-size: 12px;
	color: red;
}
.login .row i{
	width: 24px;
	height: 24px;
	line-height: 24px;
	text-align: center;
	position: absolute;
	top: 18px;
	left: 0;
	font-size: 20px;
	color: #aace52;
}
.forgetPassword{
	position: absolute;
	top: 20.5px;
	right: 0;
	font-size: 14px;
	color: #aace52;
}
.login .row input{
	width: 100%;
	height: 40px;
	border: 0;
	border-bottom: 1px solid #aace52;
	background-color: transparent;
	color: #333;
	border-radius: 0;
	padding: 0 10px 0 30px;
}
.login .row input[type=number]{
	width: 100%;
	height: 40px;
	border: 0;
	border-bottom: 1px solid #aace52;
	background-color: transparent;
	color: #333;
	border-radius: 0;
	padding: 0 10px 0 90px;
	box-sizing:border-box;
	-moz-box-sizing:border-box; /* Firefox */
	-webkit-box-sizing:border-box; /* Safari */
}
.login .row .btn{
	width: 100%;
	height: 36px;
	line-height: 36px;
	margin: 0 auto;
	border: 0;
	background-color: #eee;
	color: #999;
	border-radius: 4px;
	font-size: 16px;
	border: 0;
}
.btn::after{
	display: none;
}
.yzm {
	position: absolute;
	top: 14px;
	left: 0;
	font-size: 14px;
	width: 80px;
	height: 30px;
	line-height: 30px;
	display: block;
	color: #aace52;
	box-sizing: border-box;
	-moz-box-sizing: border-box;
	-webkit-box-sizing: border-box;
}

.getCode{
	position: absolute;
	top: 14px;
	right: 0;
	font-size: 14px;
	width: 100px;
	height: 30px;
	line-height: 30px;
	display: block;
	border: 1px solid #aace52;
	color: #aace52;
	box-sizing:border-box;
	-moz-box-sizing:border-box; /* Firefox */
	-webkit-box-sizing:border-box; /* Safari */
}
</style>
