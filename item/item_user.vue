<template>
	<!-- 用户 -->
	<mm_item :url="obj[vm.url]">
		<view class="item_user" :class="css">
			<view class="media">
				<mm_icon :src="obj[vm.avatar]" :desc="obj[vm.tip]"></mm_icon>
			</view>
			<view class="doc">
				<view class="name" v-if="obj[vm.name]"><text>{{obj[vm.name]}}</text></view>
				<view class="qrcode" v-if="obj[vm.qrcode]"></view>
				<view class="info">
					<text class="level" v-if="obj[vm.level]"><text>{{obj[vm.level]}}</text></text>
					<text class="state" v-if="obj[vm.state]"><text>{{obj[vm.state]}}</text></text>
					<text class="tag" v-if="(obj[vm.tag] && obj[vm.tag] > 0)"><text>{{obj[vm.tag]}}</text></text>
				</view>
				<view class="content" v-if="obj[vm.description]"><text>{{obj[vm.description]}}</text></view>
			</view>
		</view>
	</mm_item>
</template>

<script>
	import mixin from '@/mixins/item.js'

	export default {
		mixins: [mixin],
		data() {
			return {};
		}
	}
</script>

<style>
</style>
