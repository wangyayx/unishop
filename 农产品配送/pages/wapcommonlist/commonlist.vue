<template>
	<view>
		<view class="top">
		    <view class="shop">
		        <view class="shop_name">
					<view><i class="iconfont icon-shangdian"></i><text>萍萍麻辣烫</text></view>
		            <view class="add">北京市朝阳区世纪大道1-34号</view>
		        </view>
				<view id="weather" class="weather">
					<i class="iconfont icon-location"></i>
					<view class="city">银川</view>
				</view>
		    </view>
		</view>
		<view class="commonList">
		    <view class="title">
		        <font>常用清单</font>
		    </view>
			<view id="commonLists" class="list">
				<view v-for="(item,index) in commonList" class="listItem">
					<view class="listBox">
						<image class="listImg" :src="item.imgUrl" mode="aspectFill"></image>
						<view class="listinfo">
							<view>
								<view class="name">{{item.name}}</view>
								<view class="price">{{item.price}}元/斤</view>
							</view>
							<view class="car">
								<image onclick="changeDataGoodsCar(goodsID)" class="reduceBut" src="/static/goods_reduceBut.png"></image>
								<input onfocus="numCheckZero(this)" onblur="changeDataGoodsCarInput(goodsID,this)" onkeyup="numCheck(this)" class="nums" type="number" value="0" />
								<image onclick="changeDataGoodsCar(goodsID)" class="addBut" src="/static/goods_addBut.png"></image>
							</view>
						</view>
						
					</view>
				</view>
			</view>
		</view>
		<tab-bar :current="currentTabIndex" backgroundColor="#fff" color="#333" tintColor="#aace52" @click="tabClick"></tab-bar>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				currentTabIndex: 2,
				commonList:[{
					imgUrl: '/static/goods_pic1.png',
					name: '西兰花',
					price: '10'
				},{
					imgUrl: '/static/goods_pic2.png',
					name: '西兰花',
					price: '10'
				},{
					imgUrl: '/static/goods_pic2.png',
					name: '西兰花',
					price: '10'
				}]
			}
		},
		methods: {
			
		}
	}
</script>

<style lang="scss" scoped>
	.top{
		width: 100%;
		background-color: #aace52;
		padding: 10px;
		overflow: hidden;
		.shop{
			overflow: hidden;
			margin: 0 auto;
			font-size: 12px;
			position: relative;
			min-height: 60px;
			.shop_name{
				width: 100%;
				float: left;
				i{
					display: block;
					width: 16px;
					height: 16px;
					line-height: 16px;
					text-align: center;
					margin-top: 7px;
					float: left;
					font-size: 16px;
					color: #FFF;
				}
				text{
					width: 200px;
					line-height: 32px;
					font-size: 14px;
					color: #FFF;
					margin-left: 5px;
					text-overflow:ellipsis;
					white-space:nowrap;
					overflow:hidden;
				}
				.add{
					color: #FFF;
					line-height: 14px;
					text-overflow: ellipsis;
					white-space: nowrap;
					overflow: hidden;
					font-size: 12px;
					padding-left: 21px;
				}
			}
			.weather{
				width: 80px;
				height: 60px;
				overflow: hidden;
				position: absolute;
				right: 10px;
				text-align: center;
				.icon-location{
					width: 30px;
					height: 30px;
					line-height: 30px;
					text-align: center;
					margin: 0 auto;
					font-size: 30px;
					color: #FFF;
				}
				.city{
					color: #FFF;
					margin-top: 7px;
					font-size: 12px;
					text-overflow:ellipsis;
					white-space:nowrap;
					overflow:hidden;
				}
			}
		}
	}
	.commonList {
		.title {
		    width: 100%;
		    padding: 0 10px;
		    height: 50px;
		    line-height: 50px;
		    overflow: hidden;
		    background:#fff url(@/static/commonList_titleBg.png) no-repeat center center;
		    text-align: center;
		}
		
		.list{
			display: flex;
			flex-wrap: wrap;
			.listItem{
				width: 50%;				
				padding: 1%;
				.listBox{
					background: #fff;
					padding: 10px;
					.listImg{
						width: 100%;
						height: 160px;
						object-fit: cover;
					}
					.listinfo{
						position: relative;
						.name{
							height: 20px;
							line-height: 20px;
							font-size: 14px;
							color: #555;
							margin-top: 10px;
							text-overflow: ellipsis;
							white-space: nowrap;
							overflow: hidden;
						}
						.price{
							line-height: 30px;
							font-size: 14px;
							color: #F00;
							font-weight: 600;
						}
						.car {
						    width: 80px;
						    background-color: #eee;
						    border-radius: 10px;
							position: absolute;
							right: 10px;
							bottom: 10px;
						}
						.addBut{
							width: 20px;
							height: 20px;
							float: left;
							cursor: pointer;
						}
						.reduceBut{
							width: 20px;
							height: 20px;
							float: left;
							cursor: pointer;
						}
						.nums {
						    width: 40px;
						    height: 20px;
						    border: 0;
						    text-align: center;
						    color: #333;
						    font-size: 14px;
						    float: left;
						    background-color: transparent;
						}
					}
				}
			}
		}
		
	}
</style>
