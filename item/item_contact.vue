<template>
	<!-- 用户 -->
	<mm_item :url="obj[vm.url]">
		<view class="item_contact" :class="css">
			<view class="media">
				<mm_icon :src="obj[vm.avatar]" :desc="obj[vm.tip]"></mm_icon>
			</view>
			<view class="doc">
				<view class="name" v-if="obj[vm.name]"><text>{{obj[vm.name]}}</text></view>
				<view class="phone" v-if="obj[vm.phone]"><text>{{obj[vm.phone]}}</text></view>
			</view>
		</view>
	</mm_item>
</template>

<script>
	import mixin from '@/mixins/item.js'

	export default {
		mixins: [mixin],
		data() {
			return {
				edit: false
			};
		}
	}
</script>

<style>
</style>
