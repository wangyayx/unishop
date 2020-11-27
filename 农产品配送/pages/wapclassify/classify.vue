<template>
	<view>
		<view class="classTop">
		    <view class="search">
		        <i class="iconfont icon-sousuo"></i>
		        <input type="text" class="searchipt" placeholder="压榨胡麻油" disabled/>
		    </view>
		</view>
		<view class="oneClassify">
		    <view class="scroller">
		    	<scroll-view class="scroll-view_H" scroll-x="true" @scroll="scrollClassify" :scroll-left="scrollLeft" scroll-with-animation="true">
		    		<view v-for="(menu, indexs) in categories" :key="indexs" :class="[indexs == menuCurrentIndex ? 'menuActive' : '']" @tap="changeMenu(indexs)" class="scroll-item">{{menu.name}}</view>
		    	</scroll-view>
		    </view>
		</view>
		
		<view class="content">
			<view class="nav">
				<view class="nav-left">
					<scroll-view scroll-y :style="'height:'+height+'px'">
						<view class="nav-left-item" @click="categoryClickMain(item,index)" :key="index" :class="index==categoryActive?'active':''" v-for="(item,index) in categoryList">
							{{item.name}}
						</view>
					</scroll-view>
				</view>
				<view class="nav-right">
					<scroll-view scroll-y :scroll-top="scrollTop" @scroll="scroll" :style="'height:'+height+'px'" scroll-with-animation >
						<view :id="index==0?'first':''" class="nav-right-item" v-for="(item,index) in subCategoryList" :key="index">
							<image class="imgUrl" :src="item.imgUrl" />
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
					</scroll-view>
				</view>
			</view>
		</view>
		<tab-bar :current="currentTabIndex" backgroundColor="#fff" color="#333" tintColor="#aace52" @click="tabClick"></tab-bar>
	</view>
</template>

<script>
	export default {
		data(){
			return {
				currentTabIndex: 1,
				scrollLeft: '',
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
				categoryList:[
					{
						name:'叶菜类',
						subList:[{
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
						},{
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
						},{
							imgUrl: '/static/goods_pic2.png',
							name: '西兰花',
							price: '10'
						},{
							imgUrl: '/static/goods_pic2.png',
							name: '西兰花',
							price: '10'
						},{
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
						},{
							imgUrl: '/static/goods_pic2.png',
							name: '西兰花',
							price: '10'
						},{
							imgUrl: '/static/goods_pic2.png',
							name: '西兰花',
							price: '10'
						}]
					},
					{
						name:'特菜',
						subList:[{
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
						},{
							imgUrl: '/static/goods_pic2.png',
							name: '西兰花',
							price: '10'
						}]
					},
					{
						name:'菌类',
						subList:[{
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
						},{
							imgUrl: '/static/goods_pic2.png',
							name: '西兰花',
							price: '10'
						},{
							imgUrl: '/static/goods_pic2.png',
							name: '西兰花',
							price: '10'
						}]
					},
				],
				subCategoryList: [],
				height:0,
				categoryActive:0,
				scrollTop:0,
				scrollHeight:0,
			}
		},
		methods:{
			
			scrollClassify: function(e) {
				// this.old.scrollTop = e.detail.scrollTop
			},
			changeMenu(e){
				this.menuCurrentIndex = e
				if(e>0){
					this.scrollLeft = e*100-100
				}
			},
			scroll(e){
				this.scrollHeight = e.detail.scrollHeight;
			},
			categoryClickMain(categroy, index) {
				this.scrollTop = 0;
				this.categoryActive = index;
				this.subCategoryList = categroy.subList;
				
			},
			getCategory() {
				this.subCategoryList = this.categoryList[0].subList;
			}
		},
		onLoad:function(){
			this.getCategory()
			uni.getSystemInfo({
				success: res => {
					this.height = res.screenHeight - 149;
				}
			})
		}
	}
</script>

<style lang="scss" scoped>
	page{
		background: #fff;
	}
	.classTop{		
		height: 50px;
		position: static;
	}
	.search{
		position: fixed;
		width: 90%;
		left: 5%;
		top: 9px;
		.icon-sousuo{
			position: absolute;
			color: #666;
			width: 20px;
			height: 20px;
			line-height: 20px;
			text-align: center;
			position: absolute;
			top: 6px;
			left: 10px;
		}
		.searchipt{
			border: 1px solid #bfbfbf;
			width: 100%;
			height: 32px;
			line-height: 30px;
			font-size: 14px;
			background-color: #FFF;
			border-radius: 18px;
			padding: 0 10px 0 35px;
		}
	}
	.oneClassify{		
		position: static;
		height: 41px;		
	}
	.scroller{
		position: fixed;
		background: #fff;
		width: 100%;
		border-bottom: 1px solid #e5e5e5;
		z-index: 9;
	}
	.scroll-view_H{
		width: 100%;
		white-space: nowrap;
	}
	.scroll-item{
		display: inline-block;
		color: #333;
		font-size: 16px;
		text-align: center;
		line-height: 40px;
		margin: 0 10px;
		padding: 0 5px;
		font-size: 14px;
	}
	.menuActive{
		color: #aace52;
		height: 44px;
		line-height: 44px;
		border-bottom: 2px solid #aace52;
	}
	.nav {
		display: flex;
		width: 100%;
	}
	.nav-left {
		width: 100px;
		background-color: #f6f4f4;
		overflow-x: hidden;
		overflow-y: auto;
	}
	.nav-left-item {
		display: block;
		width: 100%;
		line-height: 50px;
		text-align: center;
		padding: 0 10px;
		font-size: 14px;
		color: #7c7c7c;
		border-bottom: 1px solid #eee;
		overflow: hidden;
	}
	.nav-right {
		flex: 1;
		background: #fff;
	}
	.nav-right-item {
		margin: 0 5px;
		padding: 15px 5px;
		overflow: hidden;
		border-bottom: 1px solid #f6f6f6;
		display: flex;
		.listinfo{
			position: relative;
			flex: 1;
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
	.nav-right-item .imgUrl{
		width: 60px;
		height: 60px;
		margin-right: 10px;
	}
	.active {
		background: #fff;
	}
	.padding {
		height: var(--status-bar-height);
		width: 100%;
		top: 0;
		position: fixed;
		background-color: #F24544;
	}
	.content {
		padding-top: var(--status-bar-height);
		width: 100%;
	}
</style>
