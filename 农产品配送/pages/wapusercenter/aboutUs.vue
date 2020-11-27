<template>
	<view class="container">
		<view class="navBar">
			<view class="navigateTop">
				<view class="iconfont icon-jiantouzuo back" @tap="back"></view>
				<text class="title">关于我们</text>
			</view>
		</view>
		<view class="aboutUs">
		    <image class="img" src="/static/customer_head.jpg" ></image>
		    <view class="version">1.0.1V 版本</view>
			<view class="aboutUl">
		        <view class="aboutItem">
		            <text>官方微信</text>
		            <text class="aboutFr">shucaiwang001</text>
		        </view>
		        <view class="aboutItem">
		            <text>官方网址</text>
		            <text class="aboutFr">http://www.shucaiwang001.com</text>
		        </view>
		        <view class="aboutItem">
		            <text>客服电话</text>
		            <text class="aboutFr">400-600-1111</text>
		        </view>
		        <view class="aboutItem">
		            <text>公司邮箱</text>
		            <text class="aboutFr">shucaiwang001@live.com</text>
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
page {
	background-color: #FFF;
}
.aboutUs{
	padding-top: 20px;
	.img {
	    width: 150px;
	    height: 150px;
	    margin: 0 auto;
		display: block;
	}
	.version{
		line-height: 50px;
		margin-bottom: 20px;
		font-size: 12px;
		color: #666;
		text-align: center;
	}
	.aboutUl{
		.aboutItem{
			width: 100%;
			height: 50px;
			line-height: 50px;
			overflow: hidden;
			padding: 0 20px;
			border-bottom: 1px solid #f0f0f0;
			display: flex;
			justify-content: space-between;
		}
		.aboutFr{
			text-align: right;
			color: #999;
			font-size: 12px;
		}
	}
} 

</style>
