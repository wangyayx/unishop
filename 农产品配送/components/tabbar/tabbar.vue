<template>
<view class="tabbar">
	<view class="tabbarlist">
		<block v-for="(item,index) in tabList" :key="index">
			<view class="navigator" :class="currentTabIndex == index ? 'on' : ''" @tap="switchTab(item.pagePath,index)">
				<view class="icon">
					<image class="iconfont" :src="currentTabIndex == index ? item.selectedIconPath : item.iconPath" mode="widthFix"></image>
					<!-- <text class="iconfont" :class="item.icon" :style="[currentTabIndex == index ? {'color': tintColor} : {'color': color}]"></text> -->
					<text v-if="item.badgeDot" class="uni_badge">{{badge}}</text>
				</view>
				<view class="text" :style="[currentTabIndex == index ? {'color': tintColor} : {'color': color}]">{{item.text}}</view>
			</view>
		</block>
	</view>
</view>
</template>

<script>
    export default {
        data() {
            return {
                tabList: [
                    {
						pagePath: "/pages/index/index",
                        iconPath: "/static/bottom_menu_1.png",
                        selectedIconPath: "/static/bottom_menu_1_hover.png",
                        text: '首页',
						badgeDot: false
                    },
                    {
						pagePath: "/pages/wapclassify/classify",
                        iconPath: "/static/bottom_menu_2.png",
                        selectedIconPath: "/static/bottom_menu_2_hover.png",						
                        text: '分类',
						badgeDot: false
                    },
                    {
						pagePath: "/pages/wapcommonlist/commonlist",
                        iconPath: "/static/bottom_menu_5.png",
                        selectedIconPath: "/static/bottom_menu_5_hover.png",
                        text: '常用清单',
						badgeDot: false
                    },
                    {
						pagePath: "/pages/wapshopping/shopping",
                        iconPath: "/static/bottom_menu_3.png",
                        selectedIconPath: "/static/bottom_menu_3_hover.png",
                        text: '购物车',
						badgeDot: true
                    },
                    {
						pagePath: "/pages/wapusercenter/usercenter",
                        iconPath: "/static/bottom_menu_4.png",
                        selectedIconPath: "/static/bottom_menu_4_hover.png",
                        text: '我的',
						badgeDot: false
                    }
                ],
				badge: '5',
                currentTabIndex: this.current
            }
        },
        props: {
            current: { type: [Number, String], default: 0 },
            color: { type: String, default: '#333' },
            tintColor: { type: String, default: '#aace52' }
        },
        methods: {
            switchTab(path,index){
				uni.reLaunch({
					url: path
				});
				// uni.switchTab({
				// 	url: path
				// });
				console.log('》》》》》》》》',path)
                this.currentTabIndex = index
                this.$emit('click', index)
            }
        },
    }
</script>

<style>
	.tabbar{
		position: static;
		height: 58px;
	}
.tabbarlist{
	display: flex;
	align-items: center;
	width: 100%;
	height: 58px;
	position: fixed;
	bottom: 0;
	left: 0;
	z-index: 2;
	background-color: #FFF;
	border-top: 8px solid #f8f8f8;
}
.navigator{
	flex: 1;
	text-align: center;
}
.icon{
	position: relative;
}
.uni_badge{
	display: block;
	width: 16px;
	height: 16px;
	line-height: 16px;
	text-align: center;
	border-radius: 50%;
	background-color: #ef4700;
	color: #FFF;
	position: absolute;
	top: -5px;
	left: 50%;
	margin-top: 1px;
	font-size: 12px;
}
.iconfont{
	width: 20px;
	height: 20px;
}
.text{
	font-size: 12px;
	color: #333;
}
</style>
