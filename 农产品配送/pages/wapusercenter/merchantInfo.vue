<template>
	<view>
		<view class="navigateTop">
		    <view class="iconfont icon-jiantouzuo back" @tap="back"></view>
		    <text class="title">商户资料</text>
		</view>
		<view class="info">
		    <view class="row">
		        <text>头像</text>
		        <image class="head" src="/static/myCenter_userHead.jpg"></image>
		    </view>
		    <view class="row">
		        <text>名称</text>
		        <text class="infostyle">萍萍麻辣烫</text>
		    </view>
		    <view class="row">
		        <text>地址</text>
		        <text class="infostyle">北京市朝阳区世纪大道1-34号</text>
		    </view>
		    <view class="row">
		        <text>电话</text>
		        <text class="infostyle">13800000000</text>
		    </view>
		</view>
		<view class="info">
		    <view class="row">
		        <text>联系人</text>
		        <text class="infostyle">张先生</text>
		    </view>
		    <view class="row">
		        <text>联系电话</text>
		        <text class="infostyle">13800000000</text>
		    </view>
		</view>
		<view class="rowbtn">
			<button class="btn" type="default" @click="loginOut()">修改密码</button>
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
			loginOut(){
				
			}
		}
	}
</script>

<style lang="scss" scoped>
.info{
	background-color: #FFF;
	margin-top: 4px;
	.row{
		line-height: 50px;
		padding: 0 10px;
		overflow: hidden;
		border-bottom: 1px solid #e5e5e5;
		display: flex;
		justify-content: space-between;
		.head{
			width: 40px;
			height: 40px;
			margin: 5px;
		}
		.infostyle{
			float: right;
			color: #999;
			text-align: right;
		}
	}
}
.rowbtn{
	position: fixed;
	bottom: 0;
	left: 0;
	width: 100%;
	.btn{
		width: 100%;
		height: 40px;
		line-height: 40px;
		text-align: center;
		background-color: #aace52;
		color: #FFF;
		display: block;
		border-radius: 0;
	}
	.btn::after{
		display: none;
	}
}
</style>
