<template>
	<view class="mm_icon" v-if="src && src.indexOf('<') !==-1" v-html="src"></view>
	<view class="mm_icon" v-else-if="src.indexOf('.') === -1"><text :class="src"></text></view>
	<view class="mm_icon" v-else-if="src">
		<image class="img" :mode="mode" :src="src" :alt="alt" :onerror="onerror" />
		<view class="figcaption" v-if="$slots.default">
			<slot></slot>
		</view>
	</view>
	<view class="mm_icon" v-else></view>
</template>

<script>
	export default {
		props: {
			mode: {
				type: String,
				default: "widthFix"
			},
			src: {
				type: String,
				default: ""
			},
			src_default: {
				type: String,
				default: "/img/default.png"
			},
			height: {
				type: String,
				default: ""
			},
			alt: {
				type: String,
				default: "图片"
			}
		},
		data() {
			return {
				ht: this.height
			}
		},
		computed: {
			onerror() {
				return "javascript:this.src='" + this.src_default + "'";
			}
		},
		onShow() {

		}
	};
</script>

<style>
</style>
