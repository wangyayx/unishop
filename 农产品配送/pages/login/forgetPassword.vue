<template>
	<view>
		<view class="navigateTop">
		    <view class="iconfont icon-jiantouzuo back" @tap="back"></view>
		    <text class="title">忘记密码</text>
		</view>
		<view class="forgetPassword">
			<view class="row">
				<input class="uni-input code" :value="code" @input="inputcode" maxlength="6" type="number" placeholder="请输入注册手机号" />
				<i class="iconfont icon-shouji"></i>
			</view>
			<view class="row">
				<input class="uni-input code" :value="code" @input="inputcode" maxlength="6" type="number" placeholder="请输入验证码" />
				<i class="iconfont icon-yanzhengma"></i>
				<text class="getCode" @tap="sendverificacode">获取验证码</text>
			</view>
			<view class="row">
				<input class="uni-input newpass" :value="newpass" @input="inputnewpass" password maxlength="12" type="text" placeholder="请输入新密码(6-12位字符)" />
				<i class="iconfont icon-mima"></i>
			</view>
			<view class="row">
				<input class="uni-input compass" :value="compass" @input="inputcompass" password maxlength="12" type="text" placeholder="确认新密码(6-12位字符)" />
				<i class="iconfont icon-mima"></i>
			</view>
			<view class="rowbtn">
				<button class="btn" type="default" @click="commitPass()">修改密码</button>
			</view>
		</view>
		
	</view>
</template>

<script>
	export default {
		data() {
			return {
				code: '',
				newpass: '',
				compass: ''
			}
		},
		methods: {
			back(){
				uni.navigateBack(1)
			},
			sendverificacode(){
				
			},
			inputcode(e){
				this.code = e.detail.value
			},
			inputnewpass(e){
				this.newpass = e.detail.value
			},
			inputcompass(e){
				this.compass = e.detail.value
			},
			commitPass(){
				console.log('>>>>>>>>>>>>>>',this.code,this.newpass,this.compass)
			}
			
		}
	}
</script>

<style lang="scss" scoped>
page {
	background-color: #FFF;
}
.forgetPassword{
	padding: 0 30px;
	.row{
		margin: 10px 0 20px;
		position: relative;
		border-bottom: 1px solid #cdcdcd;
		i{
			width: 24px;
			height: 24px;
			line-height: 24px;
			text-align: center;
			position: absolute;
			top: 8px;
			left: 0;
			font-size: 20px;
			color: #cdcdcd;
		}
		.code {
		    padding-right:90px !important;
		}
	}
	.uni-input{
		width: 100%;
		height: 40px;
		border: 0;
		border-radius: 0;
		padding-left: 30px;
		font-size: 12px;
	}
	.getCode {
	    position: absolute;
	    top: 5px;
	    right: 0;
	    font-size: 14px;
	    width: 80px;
	    height: 30px;
	    line-height: 30px;
	    display: block;
	    border: 1px solid #aace52;
	    color: #aace52;
		text-align: center;
	}
	.rowbtn{
	}
	.btn{
		width: 100%;
		height: 36px;
		line-height: 36px;
		margin: 0 auto;
		border: 0;
		background-color: #aace52;
		color: #FFF;
		font-size: 16px;
		border-radius: 4px;
		padding: 0;
	}
	.btn::after{
		display: none;
	}
}
</style>
