<template>
	<view class="mm_view" v-if="!url">
		<slot></slot>
	</view>
	<view class="mm_view" @click="openBrowser()" v-else-if="url.indexOf('http:') === 0 || url.indexOf('https:') === 0">
		<slot></slot>
	</view>
	<navigator class="mm_view" :url="url" v-else>
		<slot></slot>
	</navigator>
</template>

<script>
	export default {
		props: {
			url: {
				type: String,
				default: ""
			},
			type: {
				type: String,
				default: ""
			}
		},
		methods: {
			openBrowser() {
				if (window) {
					window.open(this.url);
				}
			}
		}
	};
</script>

<style>
</style>
