<template>
	<div>
		<qf-image-cropper :width="400" :height="400" :radius="200" @crop="handleCrop"></qf-image-cropper>
	</div>
</template>

<script>
	import QfImageCropper from '@/uni_modules/qf-image-cropper/components/qf-image-cropper/qf-image-cropper.vue';
	export default {
		components: {
			QfImageCropper
		},
		methods: {
			handleCrop(e) {
				console.log(e)
				// #ifdef H5
				var a = document.createElement('a');
				a.href = e.tempFilePath;
				a.download = new Date().valueOf() + ".png";
				a.click();
				// #endif
				// #ifndef H5
				uni.saveImageToPhotosAlbum({
					filePath: e.tempFilePath
				});
				// #endif
			}
 		}
	}
</script>

<style>

</style>
