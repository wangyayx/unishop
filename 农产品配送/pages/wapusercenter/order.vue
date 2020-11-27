<template>
	<view>
		<view class="navBar">
			<view class="navigateTop">
			    <view class="iconfont icon-jiantouzuo back" @tap="back"></view>
			    <text class="title">我的订单</text>
			</view>
		</view>
		<view class="orderMenu">
			<view class="orderMenuBox">
				<text class="orderMenuItem" :class="{ current: tabCurrentIndex == 0 }" @click="tabClick(0)">待发货</text>
				<text class="orderMenuItem" :class="{ current: tabCurrentIndex == 1 }" @click="tabClick(1)">配送中</text>
				<text class="orderMenuItem" :class="{ current: tabCurrentIndex == 2 }" @click="tabClick(2)">待付款</text>
				<text class="orderMenuItem" :class="{ current: tabCurrentIndex == 3 }" @click="tabClick(3)">已完成</text>
			</view>		    
		</view>
		<view class="list">
			<view class="order_item">
				<view class="title">
					<text class="orderNum">订单号：201805051032010001</text>
					<text class="orderTime">2018-05-05 10:32:01</text>
				</view>
				<view class="con">
					<view class="orderState">
						<text>时令水果</text>
						<text class="orderStatus">待发货</text>
					</view>
					<view class="orderGoods">
						<view class="orderGoodsItem"><image class="goodsImg" src="/static/goods_pic2.png" /></view>
						<view class="orderGoodsItem"><image class="goodsImg" src="/static/goods_pic1.png" /></view>
						<view class="orderGoodsItem"><image class="goodsImg" src="/static/goods_pic2.png" /></view>
						<view class="orderGoodsItem"><image class="goodsImg" src="/static/goods_pic2.png" /></view>
						<view class="orderGoodsItem"><image class="goodsImg" src="/static/goods_pic1.png" /></view>
						<view @tap="goOrderDetails">...共5件商品<i class="iconfont icon-jiantouyou"></i></view>
					</view>
					<view class="orderOperation">
						<view class="totalprice">10元</view>
						<view class="orderBtns">
							<view class="btn" >取消订单</view>
							<view class="btn">付款</view>							
						</view>						
					</view>
				</view>
			</view>
			<view class="moreBut">加载更多<i class="iconfont icon-jiantouxia"></i></view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				tabCurrentIndex: 0
			}
		},
		methods: {
			tabClick(e){
				this.tabCurrentIndex = e
			},
			goOrderDetails(){
				uni.navigateTo({
					url:"/pages/wapusercenter/orderDetails"
				})
			}
		}
	}
</script>

<style lang="scss" scoped>
	.orderMenu{
		position: static;
		height: 40px;
	}
	.orderMenuBox{
		overflow: hidden;
		background-color: #FFF;
		width: 100%;
		height: 40px;
		position: fixed;
		top: 50px;
		left: 0;
		display: flex;
	}
	.orderMenuBox .orderMenuItem{
		width: 20%;
		height: 40px;
		line-height: 40px;
		text-align: center;
		font-size: 14px;
		color: #050505;
	}
	.orderMenuBox .current{
		border-bottom: 2px solid #aace52;
	}
.order_item{
	.title{
		padding: 0 10px;
		height: 40px;
		line-height: 40px;
		overflow: hidden;
		font-size: 12px;
		background-color: #f1f1f1;
		display: flex;
		justify-content: space-between;
	}
	.con{
		background-color: #FFF;
		.orderState{
			padding: 0 10px;
			color: #999;
			line-height: 40px;
			overflow: hidden;
			display: flex;
			justify-content: space-between;
			.orderStatus{
				color: #ff0000;
			}
		}
		.orderGoods{
			overflow: hidden;
			padding: 5px 0;
			.orderGoodsItem{
				width: 100%;
				overflow: hidden;
				background-color: #fafafa;
				padding: 5px;
				margin: 2px 0;
				.goodsImg{
					width: 60px;
					height: 60px;
				}
			}
		}
		.orderOperation{
			padding: 0 10px;
			height: 40px;
			overflow: hidden;
			display: flex;
			justify-content: space-between;
			align-items: center;
			.totalprice{
				color: #f00;
			}
			.orderBtns{
				display: flex;
				justify-content: space-between;
				.btn{
					display: block;
					height: 24px;
					line-height: 24px;
					padding: 0 10px;
					color: #666;
					border: 1px solid #ccc;
					border-radius: 12px;
					margin-top: 7px;
					margin-left: 10px;
				}
			}
		}		
	}
	
}
.moreBut {
	width: 100%;
	line-height: 40px;
	text-align: center;
	background-color: #FFF;
	border-top: 1px solid #eee;
	padding: 0 !important;
}
</style>
