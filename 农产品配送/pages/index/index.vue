<template>
	<view class="container">
		<view class="top">
		    <view class="shop">
		        <view class="shop_name">
					<view><i class="iconfont icon-shangdian"></i><text>萍萍麻辣烫</text></view>
		            <view class="add">北京市朝阳区世纪大道1-34号</view>
		        </view>
		        <view id="weather" class="weather">
		            <i class="iconfont icon-qing"></i>
		            <p>晴天 -13℃</p>
		        </view>
		    </view>
		    <view class="search">
		        <i class="iconfont icon-sousuo"></i>
		        <input type="text" placeholder="搜索搭配、单品、用户" readonly/>
		    </view>
		</view>
		<view class="classMenu">
			<view class="classMenuItem" v-for="(item,index) in classTypes">
				<image class="classImg" :src="item.iconUrl" mode="aspectFill"></image>
				<text>{{ item.menuName }}</text>
			</view>
		</view>
		<view class="flexslider swiper">
			<view class="page-section-spacing">
				<swiper class="swiper" :indicator-dots="indicatorDots" :autoplay="autoplay" :interval="interval" :duration="duration" :indicator-color="indicatorColor" :indicator-active-color="indicatorActiveColor">
					<swiper-item v-for="(item,index) in swiperList">
						<image class="swiperImg" :src="item.imgUrl" mode="aspectFill"></image>
					</swiper-item>
				</swiper>
			</view>
		</view>
		
		<view class="commonList">
		    <view class="title">
		        <font>常用清单</font>
		    </view>
			<view class="menu">
				<view class="scroller">
					<scroll-view class="scroll-view_H" scroll-x="true" @scroll="scroll" scroll-left="120">
						<view v-for="(menu, indexs) in categories" :key="indexs" :class="[indexs == menuCurrentIndex ? 'menuActive' : '']" @tap="changeMenu(indexs)" class="scroll-item">{{menu.name}}</view>
					</scroll-view>
				</view>
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
				currentTabIndex: 0,
				classTypes:[{
					iconUrl: '/static/classMenu1.png',
					menuName: '新鲜蔬菜'
				},{
					iconUrl: '/static/classMenu2.png',
					menuName: '米面粮油'
				},{
					iconUrl: '/static/classMenu3.png',
					menuName: '时令水果'
				},{
					iconUrl: '/static/classMenu1.png',
					menuName: '水产冻货'
				},{
					iconUrl: '/static/classMenu2.png',
					menuName: '豆面制品'
				},{
					iconUrl: '/static/classMenu6.png',
					menuName: '副食品'
				},{
					iconUrl: '/static/classMenu7.png',
					menuName: '海鲜类'
				},{
					iconUrl: '/static/classMenu8.png',
					menuName: '肉蛋禽'
				}],
				swiperList: [{
					imgUrl: '/static/lbt_pic1.jpg',
				},{
					imgUrl: '/static/lbt_pic1.jpg',
				}],
				indicatorDots: true,
				autoplay: true,
				interval: 2000,
				duration: 500,
				indicatorColor: 'rgba(0, 0, 0, .25)',
				indicatorActiveColor: '#1ea838',
				menuCurrentIndex: 0,
				categories: [{
					id: 1,
					name: '肉蛋禽'
				},{
					id: 2,
					name: '豆面制品'
				},{
					id: 3,
					name: '水产冻货'
				},{
					id: 4,
					name: '时令水果'
				},{
					id: 5,
					name: '米面粮油'
				},{
					id: 6,
					name: '新鲜蔬菜'
				},{
					id: 7,
					name: '调料干货'
				}],
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
			scroll: function(e) {
				console.log(e.detail.scrollTop)
				// this.old.scrollTop = e.detail.scrollTop
			},
			changeMenu(e){
				this.menuCurrentIndex = e
			}
		}
	}
</script>

<style lang="scss" scoped>
	.container {
	}
	.top{
		width: 100%;
		background-color: #aace52;
		padding: 10px;
		overflow: hidden;
		.shop{
			overflow: hidden;
			margin: 0 auto;
			font-size: 12px;
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
			}
		}
	}
	
	.top .search{
		width: 100%;
		position: relative;
		box-sizing: border-box;
		-webkit-box-sizing: border-box;
		-moz-box-sizing: border-box;
	}
	.top .search input{
		border: 0;
		width: 100%;
		height: 40px;
		line-height: 40px;
		font-size: 14px;
		background-color: #FFF;
		border-radius: 2px;
		padding: 0 10px 0 40px;
		box-sizing:border-box;
		-moz-box-sizing:border-box; /* Firefox */
		-webkit-box-sizing:border-box; /* Safari */
	}
	.top .search i{
		width: 20px;
		height: 20px;
		line-height: 20px;
		text-align: center;
		position: absolute;
		top: 10px;
		left: 10px;
	}
	.classMenu{
		background-color: #FFF;
		overflow: hidden;
		padding: 10px 0;
	}
	.classMenuItem {
	    width: 25%;
	    padding: 10px 0;
	    float: left;
	    text-align: center;
		text{
			display: block;
			text-align: center;
			font-size: 12px;
		}
	}
	.classImg{
		width: 46px;
		height: 46px;
		margin: 0 auto;
		margin-bottom: 5px;
		border-radius: 50%;
	}
	.swiperImg{
		width: 100%;
		height: 160px;
		object-fit: cover;
	}
	.commonList {
		.title {
		    width: 100%;
		    padding: 0 10px;
		    height: 50px;
		    line-height: 50px;
		    overflow: hidden;
		    background: url(@/static/commonList_titleBg.png) no-repeat center center;
		    text-align: center;
		}
		.menu{
			position: relative;
			height: 46px;
			width: 100%;
			overflow: hidden;
			margin: 0 auto;
			background-color: #FFF;
			padding: 0 10px;
			border-bottom: 1px solid #e5e5e5;
		}
		.scroll-view_H{
			width: 100%;
			white-space: nowrap;
		}
		.scroll-item{
			width: 135px;
			display: inline-block;
			color: #333;
			font-size: 16px;
			text-align: center;
			line-height: 46px;
		}
		.menuActive{
			color: #aace52;
			height: 44px;
			line-height: 44px;
			border-bottom: 2px solid #aace52;
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
