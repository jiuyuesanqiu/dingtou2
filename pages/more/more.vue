<template>
	<view>
		<nx-cell icon="/static/oneMoneySelect.png" border title="复利计算器" @tap="goCompound"></nx-cell>
		<button open-type="contact">
			<nx-cell icon="/static/service.png" border title="意见反馈"></nx-cell>
		</button>
		<button open-type="share">
			<nx-cell icon="/static/share.png" title="分享给好友"></nx-cell>
		</button>
	</view>
</template>

<script>
	import nxCell from '../../components/nx-cell.vue';
	export default {
		data() {
			return {}
		},
		components: {
			nxCell
		},
		methods: {
			goCompound() {
				wx.navigateToMiniProgram({
					appId: 'wx02b9db6b7396855d'
				})
			},
			onShareAppMessage() {
				return {
					title: '定投计算器',
					path: '/pages/index/index'
				}
			},
		}
	}
</script>

<style>
	button {
		padding: 0;
		line-height: 1.6;
		font-size: initial;
		text-align: initial;
		border-radius: inherit;
	}

	button:after {
		border: none;
		border-radius: 0;
	}
</style>
