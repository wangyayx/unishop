<template>
	<view class="container">
		<!-- 头部区域 - 开始 -->
		<view class="myCenterTop">
			<image class="userHead" src="/static/myCenter_userHead.jpg"></image>
		    <text class="userName">萍萍麻辣烫</text>
			<view class="userset iconfont icon-shezhi" @tap="gotoSet"></view>
		</view>
		<!-- 头部区域 - 结束 -->
		
		<!-- 账户余额 - 开始 -->
		<view class="accountBalance">
			<view class="myOrderItem" @tap="gotoOrder">
				<text class="price">0.00</text>
				<text>余额</text>
			</view>
			<view class="myOrderItem" @tap="gotoOrder">
				<text class="price">0.00</text>
				<text>返利</text>
			</view>
			<view class="myOrderItem" @tap="gotoOrder">
				<text class="price">0.00</text>
				<text>欠款</text>
			</view>
			<view class="lastOrderItem" @tap="gotoOrderAllList">
				<i class="iconfont icon-daifukuan"></i>
				<text>我的钱包</text>
			</view>
		</view>
		<!-- 账户余额 - 结束 -->
		
		<!-- 我的订单 - 开始 -->
		<view class="myOrder">
			<view class="myOrderItem" @tap="gotoOrder">						
				<i class="iconfont icon-daifukuan"></i>
				<text>待付款</text>
			</view>
			<view class="myOrderItem" @tap="gotoOrder">
				<i class="iconfont icon-baoguofahuo"></i>
				<text>待发货</text>
				</view>
			<view class="myOrderItem" @tap="gotoOrder">
				<i class="iconfont icon-distribution"></i>
				<text>配送中</text>
				</view>
			<view class="myOrderItem" @tap="gotoOrder">
				<i class="iconfont icon-yishouhuo"></i>
				<text>已完成</text>
				</view>
			<view class="myOrderItem lastOrderItem" @tap="gotoOrderAllList">
				<i class="iconfont icon-dingdan"></i>
				<text>我的订单</text>
			</view>
		</view>
		<!-- 我的订单 - 结束 -->
		
		<!-- 功能菜单 - 开始 -->
		<view class="menu">
			<view class="menuItem" @tap="gotoCashCoupon"><text>优惠券</text><i class="iconfont icon-jiantouyou"></i></view>
		</view>
		<!-- 功能菜单 - 结束 -->
		
		<!-- 常用功能 - 开始 -->
		<view class="tools">
			<view class="toolsTitle">常用工具</view>
		    <view class="toolsItem">
		        <view class="toolsClunm" @tap="gotosysMessage"><i class="iconfont icon-xiaoxi1 color1"></i><text>消息中心</text></view>
		        <view class="toolsClunm" @tap="gotofeedback"><i class="iconfont icon-iconyijianfankui color2"></i><text>意见反馈</text></view>
		        <view class="toolsClunm" @tap="gotohotLine"><i class="iconfont icon-kefu1 color2"></i><text>客服热线</text></view>
		        <view class="toolsClunm" @tap="gotoaboutUs"><i class="iconfont icon-guanyuwomen color1"></i><text>关于我们</text></view>
		        <view class="toolsClunm" @tap="gotomodifyPassword"><i class="iconfont icon-lock color1"></i><text>修改密码</text></view>
		    </view>
		</view>
		<uni-popup ref="popup" type="dialog" class="dialog">
		    <uni-popup-dialog type="success" title="" content="400 600 1111" confirmcn="呼叫" :duration="2000"></uni-popup-dialog>
		</uni-popup>
		<!-- 常用功能 - 结束 -->
		<tab-bar :current="currentTabIndex" backgroundColor="#fff" color="#333" tintColor="#aace52" @click="tabClick"></tab-bar>
	</view>
	
</template>

<script>
	import tabBar from '../../components/tabbar/tabbar.vue'
	import uniPopup from '@/components/uni-popup/uni-popup.vue'
	import uniPopupMessage from '@/components/uni-popup/uni-popup-message.vue'
	import uniPopupDialog from '@/components/uni-popup/uni-popup-dialog.vue'
	export default {
		components: {
			uniPopup,
			uniPopupMessage,
			uniPopupDialog,
			tabBar
		},
		data() {
			return {
				currentTabIndex: 4
			}
		},
		methods: {
			tabClick(index){
				console.log('返回tabBar索引：' + index)
				this.currentTabIndex = index
			},
			gotoOrderAllList(){
				uni.navigateTo({
					url:"/pages/wapusercenter/order"
				})
			},
			gotoSet(){
				uni.navigateTo({
					// url: 'test?id=1&name=uniapp'  c传递参数
					url:"/pages/wapusercenter/merchantInfo"
				})
			},
			gotoCashCoupon(){
				uni.navigateTo({
					url:"/pages/wapusercenter/cashCoupon"
				})
			},
			gotosysMessage(){
				uni.navigateTo({
					url:"/pages/wapusercenter/sysMessage"
				})
			},
			gotofeedback(){
				uni.navigateTo({
					url:"/pages/wapusercenter/feedback"
				})
			},
			gotohotLine(){
				this.$refs.popup.open()
			},
			gotoaboutUs(){
				uni.navigateTo({
					url:"/pages/wapusercenter/aboutUs"
				})
			},
			gotomodifyPassword(){
				uni.navigateTo({
					url:"/pages/wapusercenter/modifyPassword"
				})
			}
		}
	}
</script>

<style lang="scss" scoped>
.myCenterTop{
	width: 100%;
	height: 160px;
	background: -webkit-linear-gradient(-45deg, #7ea420, #aace52);
	background: -o-linear-gradient(-45deg, #7ea420, #aace52);
	background: -moz-linear-gradient(-45deg, #7ea420, #aace52);
	background: linear-gradient(-45deg, #7ea420, #aace52);
	background-color: #aace52;
	background-size: cover;
	text-align: center;
	box-sizing: border-box;
	-moz-box-sizing: border-box;
	-webkit-box-sizing: border-box;
	overflow: hidden;
	border-bottom: 1px solid #e5e5e5;
	position: relative;
}
.userHead{
	width: 60px;
	height: 60px;
	margin: 0 auto;
	margin-top: 50px;
	border-radius: 50%;
	display: block;
}
.userName{
	line-height: 40px;
	font-size: 16px;
	color: #FFF;
}
.userset{
	width: 30px;
	height: 30px;
	line-height: 30px;
	text-align: center;
	border-radius: 50%;
	position: absolute;
	top: 10px;
	right: 10px;
	color: #FFF;
	font-size: 20px;
}
.accountBalance{
	background: #FFF;
	display: flex;
}
.accountBalance .lastOrderItem{
	width: 20%;
	padding: 20px 0;
	text-align: center;
	font-size: 14px;
	color: #181818;
}
.accountBalance .price{
	margin-bottom: 5px;
	font-size: 20px !important;
	color: #fa4f61;
	font-style: normal;
}
.myOrder{
	margin-top: 10px;
	background-color: #FFF;
	display: flex;
}
.myOrderItem{
	flex: 1;
	padding: 20px 0;
	text-align: center;
	font-size: 14px;
	color: #181818;
}
.lastOrderItem{	
	background: url(../../static/myOrder_bg.png) no-repeat 0 0;
}
.myOrderItem i ,.accountBalance .lastOrderItem i{
    width: 30px;
    height: 30px;
    margin: 0 auto;
    margin-bottom: 5px;
    font-size: 30px;
    color: #aace52;
}
.myOrderItem text,.accountBalance .lastOrderItem text{
	font-size: 14px;
	display: block;
}
.menu {
    margin-top: 10px;
    background-color: #FFF;
}
.menu .menuItem{
	display: flex;
	align-items: center;
	justify-content: space-between;
	width: 100%;
	height: 50px;
	line-height: 50px;
	color: #585858;
	font-size: 16px;
	padding: 0 10px;
}
.menu .menuItem i{
	color: #999;
	font-size: 16px;
	margin-right: 10px;
	float: right;
}
.tools {
    margin-top: 10px;
    background-color: #FFF;
}
.toolsTitle{
	line-height: 40px;
	padding-left: 10px;
	font-size: 16px;
	color: #000;
}
.color1{
	color: #ffc330;
}
.color2{
	color: #aace52;
}
.toolsItem{
	display: flex;
	flex-wrap: wrap;
	justify-content: space-between;
}
.toolsClunm{
	width: 25%;
	text-align: center;
	padding: 15px 0;
}
.toolsClunm i{
	font-size: 30px;
}
.toolsClunm text{
	display: block;
	font-size: 14px;
}
.dialog{
	/deep/.uni-dialog-button{
		background-color: #eee;
		color: #555;
		border-radius: 0 0 0 15px;
	}
	/deep/.uni-dialog-button.uni-border-left{
		background-color: #1ea838;
		color: #FFF;
		border-radius: 0 0 15px;
	}
	/deep/.uni-button-color{
		color: #fff;
	}
}

/* {
	background-color: #1ea838;
	color: #FFF;
	border-radius: 0 0 15px;
} */
</style>
<style>
	
</style>
