<template>
	<view>
		<view class="navBar">
			<view class="navigateTop">
			    <view class="iconfont icon-jiantouzuo back" @tap="back"></view>
			    <text class="title">商品汇总</text>
			</view>
		</view>
		<view class="collect">
			<view v-for="(item,index) in collectList" :key="index" class="list">
				<text class="name">{{item.name}}</text>
				<text class="price">{{item.price}}元/斤</text>
				<text class="nums">数量：{{item.nums}}</text>
				<text class="total">¥ {{item.price*item.nums}}元</text>
			</view>
		</view>
		<view class="settlement">
		    <view class="dis">
		        <text class="total">总价：<text class="allTotal">¥0元</text></text>
		    </view>
		    <text class="orderBtn" @tap="goSubmit">去结算</text>
		</view>
		<tab-bar :current="currentTabIndex" backgroundColor="#fff" color="#333" tintColor="#aace52" @click="tabClick"></tab-bar>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				collectList:[{
					name: '鸡蛋',
					price: '5',
					nums: '5'
				},{
					name: '鸡蛋',
					price: '5',
					nums: '5'
				},{
					name: '鸡蛋',
					price: '5',
					nums: '5'
				},{
					name: '鸡蛋',
					price: '5',
					nums: '5'
				},{
					name: '鸡蛋',
					price: '5',
					nums: '5'
				},{
					name: '鸡蛋',
					price: '5',
					nums: '5'
				},{
					name: '鸡蛋',
					price: '5',
					nums: '5'
				},{
					name: '鸡蛋',
					price: '5',
					nums: '5'
				},{
					name: '鸡蛋',
					price: '5',
					nums: '5'
				},{
					name: '鸡蛋',
					price: '5',
					nums: '5'
				},{
					name: '鸡蛋',
					price: '5',
					nums: '5'
				},{
					name: '鸡蛋',
					price: '5',
					nums: '5'
				},{
					name: '鸡蛋',
					price: '5',
					nums: '5'
				},{
					name: '鸡蛋',
					price: '5',
					nums: '5'
				},{
					name: '鸡蛋',
					price: '5',
					nums: '5'
				}]
			}
		},
		methods: {
			back(){
				uni.navigateBack(1)
			},
			goSubmit(){
				uni.navigateTo({
					url:"/pages/wapshopping/orderSubmit"
				})
			},
		}
	}
</script>

<style lang="scss">
	.collect{
		padding-bottom: 50px;
	}
	.list{
		padding: 15px 0;
		text-align: center;
		font-size: 14px;
		display: flex;
		border-bottom: 1px solid #eee;
		background-color: #FFF;
		>text{
			flex: 1;
		}
		.name{
			padding-left: 10px;
			text-align: left;
		}
		.price {
		    color: #999;
		}
		.total {
		    padding-right: 10px;
		    text-align: right;
		    color: #F00;
		}
	}
.settlement {
    width: 100%;
    height: 50px;
    line-height: 50px;
    text-align: center;
    position: fixed;
    bottom: 50px;
    left: 0;
    z-index: 3;
    border-bottom: 1px solid #e5e5e5;
	display: flex;
	justify-content: space-between;
	.dis{
		display: flex;
		justify-content: flex-end;
		flex: 1;
		height: 50px;
		line-height: 50px;
		background-color: rgba(51,51,51,.9);
		color: #FFF;
		.total {
		    height: 50px;
		    line-height: 50px;
		    margin-right: 10px;
		    text-align: right;
			.allTotal{
				color: #FFF;
				font-size: 22px;
			}
		}
	}
	.orderBtn{
	    display: block;
	    width: 120px;
	    height: 50px;
	    line-height: 50px;
	    text-align: center;
	    background-color: #aace52;
	    color: #FFF;
	    font-size: 18px;
	}
}
</style>
