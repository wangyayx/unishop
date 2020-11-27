<template>
	<view class="container">
		<view class="navigateTop">
		    <view class="iconfont icon-jiantouzuo back" @tap="back"></view>
		    <text class="title">账户余额</text>
		</view>
		
		<view class="yu_e">
		    <view class="title">账户余额</view>
		    <view class="con">¥ 0</view>
		</view>
		<view class="rowbtn">
			<button class="rechargeBut" type="default" @click="loginOut()">修改密码</button>
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
			
		}
	}
</script>

<style>
.yu_e{
	border: 1px solid #E5E5E5;
	border-radius: 5px;
	background-color: #FFF;
	margin: 5px;
}
.yu_e .title{
	line-height: 40px;
	padding-left: 10px;
	color: #666;
	border-bottom: 1px solid #E5E5E5;
}
.yu_e .con{
	line-height: 80px;
	color: #ef4700;
	font-size: 24px;
	padding-left: 10px;
}

.rechargeBut{
	margin: 5px;
	border-radius: 5px;
	height: 40px;
	line-height: 40px;
	text-align: center;
	background-color: #ef4700;
	color: #FFF;
	display: block;
}
.rechargeBut:link{
	color: #FFF;
}
.rowbtn{
	
}
</style>
