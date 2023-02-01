# qf-image-cropper
## 图片裁剪插件
uniapp微信小程序图片裁剪插件，支持自定义尺寸、定点等比例缩放、拖动、图片翻转、剪切圆形/圆角图片、定制样式，功能多性能高体验好注释全。

### 平台支持：
1. 支持微信小程序（移动端、PC端、开发者工具）
2. 支持H5平台
3. 其他平台暂未测试兼容性未知

### 支持功能：
1. 自定义裁剪尺寸
2. 定点等比例缩放：移动端以双指触摸中心点为缩放中心点，PC端以鼠标所在点为缩放中心点
3. 自由拖动：支持限制滑出边界，也支持回弹效果（滑动时可滑出边界，释放时回弹到边界）
4. 图片翻转：在裁剪尺寸非 1:1 的情况下，翻转时宽高无法铺满裁剪区域时，图片会自动放大到合适尺寸
5. 裁剪生成新图片
6. 本地选择图片
7. 可定制样式：可自由选择是否渲染裁剪边框、可伸缩裁剪顶角、参考线
8. 裁剪圆角图片：圆形、圆角矩形

### 属性说明
| 属性名 | 类型 | 默认值 | 说明 |
|:---|:---|:---|:---|
| src              | String        |         | 图片资源地址 |
| width            | Number        | 300     | 裁剪宽度 |
| height           | Number        | 300     | 裁剪高度 |
| showBorder       | Boolean       | true    | 是否绘制裁剪区域边框 |
| showGrid         | Boolean       | true    | 是否绘制裁剪区域网格参考线 |
| showAngle        | Boolean       | true    | 是否展示四个支持伸缩的角 |
| areaScale        | Number        | 0.3     | 裁剪区域最小缩放倍数 |
| maxScale         | Number        | 5       | 图片最大缩放倍数 |
| bounce           | Boolean       | true    | 是否有回弹效果：拖动时可以拖出边界，释放时会弹回边界 |
| rotatable        | Boolean       | true    | 是否支持翻转 |
| choosable        | Boolean       | true    | 是否支持从本地选择素材 |
| angleSize        | Number        | 20      | 四个角尺寸，单位px |
| angleBorderWidth | Number        | 2       | 四个角边框宽度，单位px |
| radius           | Number        |         | 裁剪图片圆角半径，单位px |
| @crop    	       | EventHandle   |         | 剪裁完成后触发，event = { tempFilePath }。在H5平台下，tempFilePath 为 base64 |

### 基本用法
```
<template>
	<div>
		<qf-image-cropper :width="500" :height="500" :radius="30" @crop="handleCrop"></qf-image-cropper>
	</div>
</template>

<script>
	import QfImageCropper from '@/components/qf-image-cropper/qf-image-cropper.vue';
	export default {
		components: {
			QfImageCropper
		},
		methods: {
			handleCrop(e) {
				// 保存到相册
				uni.saveImageToPhotosAlbum({
					filePath: e.tempFilePath
				})
			}
 		}
	}
</script>
```