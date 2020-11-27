<template>
	<view>
		<view class="navBar">
			<view class="navigateTop">
				<view class="iconfont icon-jiantouzuo back" @tap="back"></view>
				<text class="title">系统消息</text>
			</view>
		</view>
		<view class="message">
		    <view class="box">
		        <image class="img" src="/static/message_ico.png"></image>
		        <view class="dis">
		            <view class="title">系统消息</view>
		            <view class="time">2017-11-16 14:12:18</view>
		            <view class="content">系统消息暂未开放！</view>
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
			back(){
				uni.navigateBack(1)
			}
		}
	}
</script>

<style lang="scss" scoped>
.message {
	.box{
		padding: 10px;
		background-color: #FFF;
		overflow: hidden;
		border-bottom: 1px solid #eee;
		display:flex;
		.img{
			width: 24px;
			height: 24px;
			margin-right: 20px;
		}
		.dis{
			flex: 1;
			.title{
				font-size: 16px;
				color: #2f2f2f;
			}
			.time{
				font-size: 12px;
				color: #999;
			}
			.content{
				width: 90%;
				margin-top: 5px;
				background-color: #eeeeee;
				font-size: 14px;
				color: #666;
				padding: 10px;
				line-height: 24px;
			}
		}
	}
}
</style>
