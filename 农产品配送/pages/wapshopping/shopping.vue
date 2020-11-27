<template>
	<view>
		<view class="navBar">
			<view class="navigateTop">
				<text class="title">购物车</text>
				<text class="finishBut" @tap="goCollect">汇总</text>
			</view>
		</view>
		<view>
			<checkbox-group class="block" @change="changeCheckbox">
				<!-- <view :data-index="index"  class="order-item" @touchstart="drawStart" @touchmove="drawMove" @touchend="drawEnd" :style="'right:'+item.right+'px'">
					<view  class="content">列表展示内容</view>
					<view class="remove" @click="delData(item)">注 销</view>
				</view> -->
				<view v-for="(item,index) in checkboxData" :key="item.id" class="order-item" @touchstart="drawStart" @touchmove="drawMove" @touchend="drawEnd">
					<view class="order-item-info">
						<checkbox :value="String(item.id)" :checked="checkedArr.includes(String(item.id))" :class="{'checked':checkedArr.includes(String(item.id))}"></checkbox>
						<view class="right">
							<image class="goodsImg" :src="item.img" />
							<view class="dis">
								<view>{{item.name}}</view>
								<view>{{item.nuitprice}}元/斤</view>
								<view>小计：<text class="color">¥20.00元</text></view>
							</view>
						</view>
						
					</view>
					<!-- <view class="remove">删除</view> -->
				</view>
			</checkbox-group>
		</view>
		<view class="settlement">
		    <view class="dis">
				<view>
					<checkbox-group @change="allChoose">
						<label>
							<checkbox value="all" class="checkedAll" :class="{'checked':allChecked}" :checked="allChecked?true:false"></checkbox> 全选
						</label>
					</checkbox-group>
				</view>
		        <text class="total">合计：<text class="allTotal">¥0元</text></text>
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
				currentTabIndex: 3,
				isChecked:false,
				checkboxData:[{
					id: 1,
					img: '/static/goods_pic2.png',
					name: '鸡蛋',
					nuitprice: '10'
				},{
					id: 2,
					img: '/static/goods_pic2.png',
					name: '鸡蛋',
					nuitprice: '10'
				}],
				checkedArr:[], //复选框选中的值
				allChecked:false, //是否全选
				csListArrl:[],
				delBtnWidth: 160
			}
		},
		methods: {
			goCollect(){
				uni.navigateTo({
					url:"/pages/wapshopping/collect"
				})
			},
			goSubmit(){
				uni.navigateTo({
					url:"/pages/wapshopping/orderSubmit"
				})
			},
			//开始触摸滑动
			drawStart(e) {
				console.log("开始触发");
				var touch = e.touches[0];
				this.startX = touch.clientX;
			},
			//触摸滑动
			drawMove(e) {
				console.log("滑动");
				for (var index in this.csListArrl) {
					this.$set(this.csListArrl[index],'right',0);
				}
				var touch = e.touches[0];
				var item = this.csListArrl[e.currentTarget.dataset.index];
				var disX = this.startX - touch.clientX;
				if (disX >= 20) {
					if (disX > this.delBtnWidth) {
						disX = this.delBtnWidth;
					}
				this.$set(this.csListArrl[e.currentTarget.dataset.index],'right',disX);
				} else {
					this.$set(this.csListArrl[e.currentTarget.dataset.index],'right',0);
				}
			},
			//触摸滑动结束
			drawEnd(e) {
				console.log("滑动结束");
				var item = this.csListArrl[e.currentTarget.dataset.index];
				if (item.right >= this.delBtnWidth / 2) {
					this.$set(this.csListArrl[e.currentTarget.dataset.index],'right',this.delBtnWidth);
				} else {
					this.$set(this.csListArrl[e.currentTarget.dataset.index],'right',0);
				}
			},
			// 多选复选框改变事件
			changeCheckbox(e){
				this.checkedArr = e.detail.value;
				// 如果选择的数组中有值，并且长度等于列表的长度，就是全选
				if(this.checkedArr.length>0 && this.checkedArr.length==this.checkboxData.length){
					this.allChecked=true;
				}else{
					this.allChecked=false;
				}
			},
			// 全选事件
			allChoose(e){
				let chooseItem = e.detail.value;
				// 全选
				if(chooseItem[0]=='all'){
					this.allChecked=true;
					for(let item of this.checkboxData){
						let itemVal=String(item.value);
						if(!this.checkedArr.includes(itemVal)){
							this.checkedArr.push(itemVal);
						}
					}                    
				}else{
					// 取消全选
					this.allChecked=false;
					this.checkedArr=[];
				}
			}
		}
	}
</script>

<style lang="scss">
	.order-item{
		margin-top: 4px;
		background-color: #FFF;
		overflow: hidden;
		padding: 10px;
		.order-item-info{
			display: flex;
			align-items: center;
			.right{
				display: flex;
				.goodsImg{
					width: 80px;
					height: 80px;
					margin-right: 10px;
				}
				.dis{
					line-height: 24px;
					font-size: 14px;
					text-overflow: ellipsis;
					white-space: nowrap;
					overflow: hidden;
				}
				.color{
					color: #ef4700;
				}
			}
		}
	}
	.finishBut {
	    width: 32px;
	    color: #aace52;
	    text-align: right;
	    right: 20px;
		top: 15.5px;
	    font-size: 14px;
		position: absolute;
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
		justify-content: space-between;
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
	
	.checkedAll{
		margin-left: 10px;
	}
}
</style>

