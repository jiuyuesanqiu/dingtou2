<template>
	<button open-type="share" class="share bg-yellow text-white shadow">
		<text class="cuIcon-forward"></text>
	</button>
</template>

<script>
	export default {
		data() {
			return {
				
			};
		}
	}
</script>

<style>
	.share {
		width: 100upx;
		height: 100upx;
		border-radius: 50%;
		border: none;
		position: fixed;
		z-index: 9999;
		bottom:150upx;
		left: 43%;
	}

	button::after {
		border: none;
	}
</style>
