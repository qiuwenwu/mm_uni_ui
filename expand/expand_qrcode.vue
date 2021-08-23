<template>
	<view class="expand_qrcode">
		<!-- #ifndef MP-ALIPAY -->
		<canvas class="expand_qrcode-canvas" :canvas-id="ide" :style="{width: se + 'px', height: se + 'px'}" />
		<!-- #endif -->
		<!-- #ifdef MP-ALIPAY -->
		<canvas :id="ide" :width="se" :height="se" class="expand_qrcode-canvas" />
		<!-- #endif -->
		<image v-show="show" :src="result" :style="{width: se + 'px', height: se + 'px'}" />
	</view>
</template>

<script>
	import QRCode from "@/plugins/qrcode.js"
	let qrcode;
	export default {
		name: "expand_qrcode",
		props: {
			ide: {
				type: String,
				default: "expand_qrcode"
			},
			value: {
				type: String,
				default: ""
			},
			icon: {
				type: String,
				default: ""
			},
			url: {
				type: String,
				default: ""
			},
			height: {
				type: Number,
				default: 0
			},
			background: {
				type: String,
				default: '#ffffff'
			},
			foreground: {
				type: String,
				default: '#000000'
			},
			iconRadius: {
				type: Number,
				default: 10
			},
			iconBorderWidth: {
				type: Number,
				default: 3
			},
			size: {
				type: Number,
				default: 200
			},
			unit: {
				type: String,
				default: 'upx'
			},
			show: {
				type: Boolean,
				default: true
			},
			pdground: {
				type: String,
				default: '#000000'
			},
			icon: {
				type: String,
				default: ''
			},
			iconSize: {
				type: Number,
				default: 40
			},
			lv: {
				type: Number,
				default: 3
			},
			onval: {
				type: Boolean,
				default: false
			},
			showLoading: {
				type: Boolean,
				default: true
			},
			loadingText: {
				type: String,
				default: '二维码生成中'
			}
		},
		data() {
			return {
				result: ''
			}
		},
		methods: {
			new_qrcode() {
				let _this = this;
				qrcode = new QRCode({
					context: this, // 上下文环境
					canvasId: this.ide, // canvas-id
					usingComponents: true, // 是否是自定义组件
					showLoading: this.showLoading, // 是否显示loading
					loadingText: this.loadingText, // loading文字
					text: this.value || this.url, // 生成内容
					size: this.se, // 二维码大小
					background: this.background, // 背景色
					foreground: this.foreground, // 前景色
					pdground: this.pdground, // 定位角点颜色
					correctLevel: this.lv, // 容错级别
					image: this.icon, // 二维码图标
					imageSize: this.iconSize, // 二维码图标大小
					cbResult: function(res) { // 生成二维码的回调
						_this.$emit('result', res)
						_this.result = res;
					},
				});
			},
			clear_qrcode() {
				this.$emit('result', '')
				this.result = '';
				qrcode.clear()
			},
			save_qrcode() {
				if (this.result != "") {
					uni.saveImageToPhotosAlbum({
						filePath: this.result,
						success: function() {
							uni.showToast({
								title: '二维码保存成功',
								icon: 'success',
								duration: 2000
							});
						}
					});
				}
			}
		},
		watch: {
			url() {
				this.new_qrcode()
			},
			value() {
				this.new_qrcode()
			}
		},
		computed: {
			se() {
				if (this.unit == "upx") {
					return uni.upx2px(this.size)
				} else {
					return this.size
				}
			}
		},
		mounted: function() {
			this.$nextTick(() => {
				this.new_qrcode()
			});
		}
	}
</script>

<style>
	.expand_qrcode {
		position: relative;
		margin: auto;
	}

	.expand_qrcode-canvas {
		position: fixed;
		top: -99999upx;
		left: -99999upx;
		z-index: -99999;
	}
	
	.expand_qrcode canvas {
		margin: auto;
	}
	
	.expand_qrcode image {
		margin: auto;
	}
	
	.expand_qrcode {
		text-align: center;
	}
</style>
