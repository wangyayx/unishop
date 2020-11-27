<template>
	<view>
		<view class="navBar">
			<view class="navigateTop">
				<view class="iconfont icon-jiantouzuo back" @tap="back"></view>
				<text class="title">优惠券</text>
			</view>
		</view>
		<view class="cashCoupon">
		    <view class="box">
		         <view class="top"></view>
		         <view class="midd">
		             <view class="money"><text>100</text>元</view>
		             <view class="dis">
		                 <text class="h1">代金券</text>
		                 <text class="h3">满100减5元</text>
		                 <text class="p">使用期限：2016.10.16 ~ 2017.08.12</text>
		             </view>
		         </view>
		         <view class="bot"></view>
		     </view>
		     <view class="box overdue">
		         <view class="top"></view>
		         <view class="midd">
		             <view class="money"><text>100</text>元</view>
		             <view class="dis">
		                 <text class="h1">代金券</text>
		                 <text class="h3">满100减5元</text>
		                 <text class="p">使用期限：2016.10.16 ~ 2017.08.12</text>
		             </view>
		         </view>
		         <view class="bot"></view>
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
			
		}
	}
</script>

<style lang="scss" scoped>
.cashCoupon{
	margin-top: 5px;
	.box{
		margin: 0px 5px 10px 5px;
		.top{
			width: 100%;
			height: 9px;
			background: url(/static/cashCoupon_topBg.png) repeat-x center;
		}
		.bot{
			width: 100%;
			height: 15px;
			background-color: #aace52;
			border-radius: 0 0 10px 10px;
		}
	}
}
.midd{
	width: 100%;
	background-color: #FFF;
	overflow: hidden;
	display: flex;
	.money{
		width: 100px;
		height: 100px;
		line-height: 100px;
		text-align: center;
		color: #aace52;
		border-right: 1px dashed #aace52;
		margin-right: 20px;
	}
	.money text{
		font-size: 40px;
	}
	.dis{
		flex: 1;;
		padding-top: 20px;
		height: 100px;
		float: right;
		background-size: 150px 150px;
		background-position: top 20px right -40px;
	}
	.dis .h1{
		line-height: 20px;
		color: #aace52;
		font-size: 16px;
	}
	.dis .h3{
		line-height: 20px;
		color: #666;
		font-size: 14px;
	}
	.dis .p{
		line-height: 20px;
		color: #b6b6b6;
		font-size: 12px;
	}
}

.overdue .midd .dis .h1,.overdue .midd .dis .h3,.overdue .midd .money{
	color: #b6b6b6;
}
.overdue {
	.bot{
		background-color: #a1a1a1;
	}
	.midd .dis{
		background-size: 150px 150px;
		background-position: top 20px right -40px;
	}
}
</style>
