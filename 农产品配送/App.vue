<script>
export default {
	onLaunch: function() {
		console.log('App Launch');
	},
	onShow: function() {
		console.log('App Show');
	},
	onHide: function() {
		console.log('App Hide');
	}
};
</script>

<style lang="scss">
@import url("/static/fonts/iconfont.css");
/* 解决头条小程序组件内引入字体不生效的问题 */
/* #ifdef MP-TOUTIAO */
@font-face {
	font-family: uniicons;
	src: url('/static/uni.ttf');
}
/* #endif */
*{
	box-sizing: border-box;
	-moz-box-sizing: border-box;
	-webkit-box-sizing: border-box;
}
body{
	background-color: #F1F1F1;
	font-size: 14px;
	font-family: "Microsoft YaHei","微软雅黑";
	color: #333333;
	-webkit-text-size-adjust: 100%;
	-ms-text-size-adjust: 100%;
	-webkit-tap-highlight-color:rgba(0,0,0,0);
}
.navBar{
	height: 50px;
	position: static;
}
.navigateTop{
	position: fixed;
	top: 0;
	width: 100%;
	height: 50px;
	padding: 0 10px;	
	overflow: hidden;
	background-color: #FFF;
	border-bottom: 1px solid #f1f1f1;
	z-index: 99;
	.back{
		width: 32px;
		height: 17px;
		color: #aace52;
		position: absolute;
		top: 16.5px;
	}
	.title{
		height: 50px;
		line-height: 50px;
		text-align: center;
		color: #000;
		font-size: 16px;
		width: 100%;
		display: block;
	}
}
	uni-checkbox .uni-checkbox-input{
		border-radius: 50%;
		background-color: transparent;
		width: 16px;
		height: 16px;
	}
	uni-checkbox .uni-checkbox-input.uni-checkbox-input-checked{
		color: #aace52 !important;
		border-color: #aace52 !important;
	}
	uni-checkbox:not([disabled]) .uni-checkbox-input:hover{
		color: #aace52 !important;
		border-color: #aace52 !important;
	}
</style>
