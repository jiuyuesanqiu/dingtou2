<template>
	<view class="d-flex fuli-cell" hover-class="fuli-cell-active">
		<view class="fuli-cell-left d-flex align-items-center">
			<image class="fuli-cell-icon" :src="icon"></image>
		</view>
		<view class="fuli-cell-right flex-grow-1 d-flex" :class="border?'border-b':''">
			<view class="flex-grow-1">
				<text>{{title}}</text>
			</view>
			<text color="#888888" class="cuIcon-right"></text>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {

			};
		},
		props: {
			icon: String,
			title: String,
			border: {
				type: Boolean,
				value: true
			}
		},
		methods: {}
	}
</script>

<style>
	.fuli-cell {
		background: white;
		color: #353535;
	}

	.fuli-cell-left {
		padding: 31rpx 36rpx;
	}

	.fuli-cell-right {
		font-size: 36rpx;
		padding: 31rpx 26rpx 31rpx 0;
	}

	.fuli-cell-icon {
		width: 40rpx;
		height: 40rpx;
	}

	.fuli-cell-active {
		background-color: #e5e5e5;
	}

	.border-b {
		border-bottom: 1rpx solid #eee;
	}
</style>
