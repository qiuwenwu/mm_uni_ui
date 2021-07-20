<template>
	<!-- 基础 -->
	<mm_item :url="obj[vm.url]">
		<view class="item_base" :class="css">
			<view class="media" v-if="icon_key">
				<mm_icon class="img" :src="obj[vm[icon_key]]" :src_default="src_default"></mm_icon>
			</view>
			<view class="doc">
				<view class="title" v-html="obj[vm.title]"></view>
				<view class="content" v-html="obj[vm.content]" v-if="obj[vm.content]"></view>
			</view>
			<slot></slot>
		</view>
	</mm_item>
</template>

<script>
	import mixin from '@/mixins/item.js'

	export default {
		mixins: [mixin],
		props: {
			icon_key: {
				type: String,
				default: ""
			}
		},
		data() {
			return {};
		}
	}
</script>

<style>
</style>
