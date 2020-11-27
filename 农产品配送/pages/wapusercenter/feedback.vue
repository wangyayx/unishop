<template>
	<view>
		<view class="navBar">
			<view class="navigateTop">
			    <view class="iconfont icon-jiantouzuo back" @tap="back"></view>
			    <text class="title">意见反馈</text>
			</view>
		</view>
		<view class="yu_e">
		    <textarea class="feedbackText" v-model="content" maxlength="150" @input="conInput" placeholder="请输入您的反馈意见(字数150字以内)"></textarea>
		    <view class="textNum"><text id="nowNums">{{tatVal}}</text>/150</view>
		</view>
		<view class="rowbtn">
			<button class="btn" type="default" :class="btnActive">提交反馈</button>
		</view>
		
	</view>
</template>

<script>
	export default {
		data() {
			return {
				content:'',
				tatVal: 0,
				btnActive: ''
			}
		},
		methods: {
			conInput(){
				this.tatVal = this.content.length;
				if(this.tatVal > 0){
					this.btnActive = 'btnActive'
				} else {
					this.btnActive = ''
				}
			},
		}
	}
</script>

<style lang="scss" scoped>
	.yu_e{
		border: 1px solid #E5E5E5;
		border-radius: 5px;
		background-color: #FFF;
		margin: 5px;
		overflow: hidden;
		position: relative;
	}
	.feedbackText{
		padding: 10px;
	}
	.rowbtn{
		padding: 0 5px;
	}
	.btn{
		width: 100%;
		height: 40px;
		line-height: 40px;
		margin: 0 auto;
		border: 0;
		background-color: #ccc;
		color: #FFF;
		font-size: 16px;
		border-radius: 4px;
		padding: 0;
	}
	.btnActive{
		background: #ef4700;
	}
	.btn::after{
		display: none;
	}
.textNum{
	position: absolute;
	bottom: 5px;
	right: 10px;
	color: #ef4700;
}
</style>
