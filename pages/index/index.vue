<template>
	<view class="content">
		<!-- 头部 -->
		<view class="navbar">
			<view v-for="(item, index) in navList" :key="index" class="nav-item" :class="{ current: tabCurrentIndex === index }"
			 @click="tabClick(index)">
				{{ item.text }}
			</view>
		</view>
		<!-- 显示区域 -->
		<view class="list" v-for="(item, index) in navList" :key="index" v-if="tabCurrentIndex === index">
			<view class="listF" v-for="(itemIn,index) in item.orderList" :key="index">
				<view class="listTit">
					<view class="titName"><label class="listIcon">图标111</label>{{itemIn.name}}></view>
					<view class="titState">{{itemIn.stateIn}}</view>
				</view>
				<view class="listDel">
					<view class="listImg"><image src="../../static/logo.png" mode=""></image></view>
					<view class="listCont">
						<view class="goodsName">{{itemIn.name}}</view>
						<view class="firstDate">{{itemIn.dateA}}</view>
						<view class="inDate">{{itemIn.dateB}}</view>
						<view class="lastDate">{{itemIn.dateC}}</view>
					</view>
					<view class="price">￥{{itemIn.price}}</view>
				</view>
				<view class="listBtn">
					<view class="btn" :class="{hide: itemIn.stateIn == 3 }">再来一单</view>
					<view class="btn" :class="{ btnLight: itemIn.stateIn == 2 }">分享得5积分</view>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				title: 'Hello',
				tabCurrentIndex: 0,
				navList: [{
						state: 0,
						text: '全部',
						orderList: [
							{
								stateIn:'1',
								name:'店铺名称',
								price:'178.00',
								dateA:'2021-04-15 12:20:45',
								dateB:'2021-04-15 12:20:45',
								dateC:'2021-04-15 12:20:45',
							},
							{
								stateIn:'2',
								name:'店铺名称',
								price:'178.00',
								dateA:'2021-04-15 12:20:45',
								dateB:'2021-04-15 12:20:45',
								dateC:'2021-04-15 12:20:45',
							},
							{
								stateIn:'3',
								name:'店铺名称',
								price:'178.00',
								dateA:'2021-04-15 12:20:45',
								dateB:'2021-04-15 12:20:45',
								dateC:'2021-04-15 12:20:45',
							}
						]
					},
					{
						state: 1,
						text: '待下单',
						orderList: []
					},
					{
						state: 2,
						text: '待结算',
						orderList: []
					},
					{
						state: 3,
						text: '已结算',
						orderList: []
					},
					{
						state: 4,
						text: '已作废',
						orderList: []
					}
				]
			}
		},
		onLoad() {
			this.tabCurrentIndex = 0;
		},
		methods: {
			changeTab(e) {
				this.tabCurrentIndex = e.target.current;
			},
			//顶部tab点击
			tabClick(index) {
				this.tabCurrentIndex = index;
			}
		}
	}
</script>

<style>
	page,
	.content {
		background: #F1F1F1;
		height: 100%;
		font-size: 16px;
		color: #000000;
		font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
	}
	.navbar {
		display: flex;
		height: 40px;
		padding: 0 5px;
		background: #fff;
		box-shadow: 0 1px 5px rgba(0, 0, 0, 0.06);
		position: relative;
		z-index: 10;
	}
	.nav-item {
		flex: 1;
		display: flex;
		justify-content: center;
		align-items: center;
		height: 100%;
		font-size: 15px;
		color: #000000;
		position: relative;
	}
	.current {
		color: #007AFF;
	}
	.current:after {
		content: '';
		position: absolute;
		left: 50%;
		bottom: 0;
		transform: translateX(-50%);
		width: 44px;
		height: 0;
		border-bottom: 2px solid #007AFF;
	}
	
	.listF{
		margin: 10px;
		background: #FFFFFF;
		border-radius: 10px;
	}
	.listTit{
		padding: 15px;
		border-bottom: 1px solid #F1F1F1;
		display: flex;
		justify-content: space-between;
	}
	
	.listDel{
		padding: 15px;
		display: flex;
		justify-content: space-between;
	}
	.listImg{
		width: 100px;
		height: 100px;
		border-radius: 10px;
		overflow: hidden;
	}
	.listImg image{
		width: 100%;
		height: 100%;
	}
	.listCont{
		color: #C8C7CC;
		font-size: 14px;
		line-height: 25px;
		position: absolute;
		left: 135px;
	}
	.goodsName,.price{
		color: #000000;
		font-weight: bold;
	}
	.price{
		
	}
	.listBtn{
		line-height: 40px;
		padding: 15px;
		display: flex;
		justify-content: flex-end;
	}
	.hide{
		display: none;
	}
	.listBtn .btn{
		border: 1px solid #C0C0C0;
		border-radius: 20px;
		padding: 0 10px;
		margin: 0 10px;
	}
	.listBtn .btn:last-child{
		margin: 0;
	}
	.btnLight{
		border: 1px solid #F0AD4E !important;
		color: #F0AD4E;
	}
</style>
