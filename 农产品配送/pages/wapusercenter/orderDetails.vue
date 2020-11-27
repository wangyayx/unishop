<template>
	<view>
		<view class="navBar">
			<view class="navigateTop">
				<view class="iconfont icon-jiantouzuo back" @tap="back"></view>
				<text class="title">订单详情</text>
			</view>
		</view>
		<view class="orderDetails">
			<view class="orderState">
				<view class="orderNum">订单号：201805051032010001</view>
				<view class="state">代发货</view>
			</view>
			<view class="goodsList" :class="foldClass">
				<view class="goodsListItem" v-for="(item,index) in goodsList" :key="index">
					<view class="goodsInfo">
						<image class="imgUrl" :src="item.img" />
						<view class="dis">
							<view class="name">{{ item.name }}</view>
							<view class="unit">¥ {{ item.unit }}元/斤</view>
							<view class="price">共：<text>¥{{ item.price }}元</text></view>
						</view>
					</view>
					<view class="inforemarks">商品备注：暂无</view>
				</view>
			</view>
			<view class="spread" @tap="btnflod" v-if="fold">展开其余商品<i class="iconfont icon-jiantouxia"></i></view>
			<view class="spread" @tap="btnflod" v-if="!fold">收起<i class="iconfont icon-jiantoushang"></i></view>
			<view class="totalDis">小计：<text class="red">100 元</text></view>
			<view class="userDis">
				<view class="userDisItem"><text>收货人：</text><text>王小二</text></view>
				<view class="userDisItem"><text>收货地址：</text><text>北京市朝阳区新华路玉书巷3-5号</text></view>
				<view class="userDisItem"><text>联系电话：</text><text>13700000000</text></view>
				<view class="userDisItem"><text>下单时间：</text><text>2018-05-05 10:32:01</text></view>
				<view class="userDisItem"><text>配送时间：</text><text>2018-05-05 10:32:01</text></view>
			</view>
			<view class="remarks">
				备注：暂无
			</view>
		</view>		
		<view class="settlement">
		    <view class="dis">
		        <text class="total">实际付款：<text class="allTotal">¥0元</text></text>
		    </view>
		    <text class="orderBtn">付款</text>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				fold:true,
				foldClass: '',
				goodsList:[{
					img: '/static/goods_pic2.png',
					name: '西兰花',
					unit: '10',
					price: '10'
				},{
					img: '/static/goods_pic2.png',
					name: '西兰花',
					unit: '10',
					price: '10'
				},{
					img: '/static/goods_pic2.png',
					name: '西兰花',
					unit: '10',
					price: '10'
				},{
					img: '/static/goods_pic2.png',
					name: '西兰花',
					unit: '10',
					price: '10'
				},{
					img: '/static/goods_pic2.png',
					name: '西兰花',
					unit: '10',
					price: '10'
				},{
					img: '/static/goods_pic2.png',
					name: '西兰花',
					unit: '10',
					price: '10'
				},{
					img: '/static/goods_pic2.png',
					name: '西兰花',
					unit: '10',
					price: '10'
				},{
					img: '/static/goods_pic2.png',
					name: '西兰花',
					unit: '10',
					price: '10'
				},{
					img: '/static/goods_pic2.png',
					name: '西兰花',
					unit: '10',
					price: '10'
				}]
			}
		},
		methods: {
			btnflod(){
				this.fold=!this.fold;
				if(!this.fold){
					this.foldClass = 'goodsmaxh'
				}
			},
			back(){
				uni.navigateBack(1)
			}
		}
	}
</script>

<style lang="scss" scoped>
	.orderDetails{
		padding-bottom: 65px;
	}
	.goodsList {
	    overflow: hidden;
	    background-color: #FFF;
		max-height: 340px;
		.goodsListItem{
			padding: 10px;
			overflow: hidden;
			font-size: 14px;
			margin: 2px 0;
			.goodsInfo{
				display: flex;
				.dis{
					position: relative;
					flex: 1;
				}
				.name{
					
				}
				.unit{
					line-height: 20px;
					margin-top: 20px;
					color: #999;
				}
				.price{
					position: absolute;
					right: 10px;
					top: 0;
					text{
						color: #F00;
					}
				}
			}
			.imgUrl{
				width: 60px;
				height: 60px;
				margin-right: 20px;
			}
			.inforemarks {
			    line-height: 30px;
			    text-overflow: ellipsis;
			    white-space: nowrap;
			    overflow: hidden;
			    background-color: transparent;
			}
		}
	}
	.goodsmaxh{
		max-height: none !important;
	}
	.orderState{
		padding: 0 10px;
		color: #999;
		line-height: 40px;
		overflow: hidden;
		display: flex;
		justify-content: space-between;
		.state{
			color: #ff0000;
		}
	}
	.spread {
	    display: block;
	    width: 100%;
	    background-color: #FFF;
	    line-height: 40px;
	    text-align: center;
	    border-top: 1px solid #e5e5e5;
	    color: #999;
	}
.totalDis{
	height: 40px;
	line-height: 40px;
	padding: 0 10px;
	text-align: right;
	background-color: #FFF;
	.red{
		color: #ef4700;
	}
}
.userDis{
	background-color: #FFF;
	padding: 0 10px;
	margin-top: 4px;
	.userDisItem{
		line-height: 30px;
		font-size: 14px;
		color: #030303;
		overflow: hidden;
		
	}
	.userDisItem text:first-child{
		width: 70px;
		color: #999;
		display: inline-block;
	}
}
.remarks {
    width: 100%;
    height: 80px;
    border: 0;
    margin-top: 4px;
    line-height: 20px;
    padding: 5px 10px;
    color: #666;
	background: #fff;
}
.settlement {
    width: 100%;
    height: 50px;
    line-height: 50px;
    text-align: center;
    position: fixed;
    bottom: 0;
    left: 0;
    z-index: 3;
    border-bottom: 1px solid #e5e5e5;
	display: flex;
	justify-content: space-between;
	.dis{
		display: flex;
		flex: 1;
		height: 50px;
		line-height: 50px;
		background-color: rgba(51,51,51,.9);
		color: #FFF;
		.total {
		    height: 50px;
		    line-height: 50px;
		    margin-left: 10px;
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
