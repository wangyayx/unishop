<template>
	<view>
		<view class="navBar">
			<view class="navigateTop">
				<view class="iconfont icon-jiantouzuo back" @tap="back"></view>
				<text class="title">提交订单</text>
			</view>
		</view>
		<view class="orderDetails">
			<view class="position">
				<view class="ico">
					<image class="img" src="/static/orderSubmit_dw_ico.png">
					<view class="icotit">定位</view>
				</view>
				<view class="address">
					<view class="title">张小二　　13800000000</view>
					<view class="m_top">北京市朝阳区新华路玉书巷3-5号</view>
				</view>
			</view>
			<hTimePicker sTime="06" cTime="19" interval="15" dayNum="1" @changeTime="changeTime">
				<view class="logistics" slot="pCon">
					<view class="logisticslf">
						<view>包裹：由农副产品配送配送</view>
						<view><text class="color">期望送达时间：</text> 2020-11-28 08:30</view>		        
					</view>
					<i class="iconfont icon-jiantouyou"></i>
				</view>
			</hTimePicker>
			<view class="goodsList" :class="foldClass">
				<view class="goodsListItem" v-for="(item,index) in goodsList" :key="index">
					<view class="goodsInfo">
						<image class="imgUrl" :src="item.img" />
						<view class="dis">
							<view class="name">{{ item.name }}</view>
							<view class="unit">¥ {{ item.unit }}元/斤</view>
							<view class="price">共：2斤/<text>¥{{ item.price }}元</text></view>
						</view>
					</view>				
				</view>
			</view>
			<view class="spread" @tap="btnflod" v-if="fold">展开其余商品<i class="iconfont icon-jiantouxia"></i></view>
			<view class="spread" @tap="btnflod" v-if="!fold">收起<i class="iconfont icon-jiantoushang"></i></view>
			<view class="remarks">
				<textarea placeholder="请输入订单备注"/>
			</view>
		</view>
		
		<view class="settlement">
		    <view class="dis">
		        <text class="total">实际付款：<text class="allTotal">¥0元</text></text>
		    </view>
		    <text class="orderBtn">去结算</text>
		</view>
		
	</view>
</template>

<script>
	import hTimePicker from "@/components/h-timePicker/h-timePicker.vue";
	export default {
		components: { hTimePicker },
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
			changeTime(e,i){
				console.log('>>>>>>>>>>>',e,i)
			},
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
	.position{
		overflow: hidden;
		background-color: #FFF;
		display: flex;
	}
	.position .ico{
		text-align: center;
		font-size: 12px;
		color: #1c1c1c;
		padding: 10px;
		margin-right: 10px;
		.img{
			width: 28px;
			height: 28px;
			margin-bottom: 5px;
		}
	}
	.position .address{
		float: right;
		min-height: 59px;
		padding: 10px 10px 10px 0;
		.title{
			font-size: 14px;
			color: #1c1c1c;
			text-overflow:ellipsis;
			white-space:nowrap;
			overflow:hidden;
		}
		.m_top{
			line-height: 20px;
			font-size: 14px;
			color: #1c1c1c;
			margin-top: 0px;
			display: -webkit-box;
			-webkit-box-orient: vertical;
			-webkit-line-clamp: 2;
			overflow: hidden;
		}
	}
	.logistics{
		overflow: hidden;
		background-color: #FFF;
		margin-top: 4px;
		display: flex;
		justify-content: space-between;
		.logisticslf{
			float: left;
			padding: 5px 10px;
			.color{
				color: #999;
			}
		}
		.logisticslf view{
			line-height: 24px;
			font-size: 14px;
			color: #1c1c1c;
			text-overflow:ellipsis;
			white-space:nowrap;
			overflow:hidden;
			
		}
		
	}
	.logistics i{
		float: right;
		font-size: 14px;
		margin-top: 21.5px;
		margin-right: 10px;
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
					color: #999;
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
	.remarks{
		width: 100%;
		height: 80px;
		border: 0;
		margin-top: 4px;
		line-height: 20px;
		padding: 5px 10px;
		color: #666;
		background: #fff;
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
