<template>
	<!-- 号码 -->
	<mm_item :url="obj[vm.url]">
		<view class="item_number" :class="css">
			<view class="doc">
				<text class="phone" v-if="obj[vm.phone]"><text>{{obj[vm.phone]}}</text></text>
				<text class="type" v-if="obj[vm.type]"><text>{{obj[vm.type]}}</text></text>
				<view class="content">
					<text class="date" v-if="obj[vm.date]"><text>{{obj[vm.date]}}</text></text>
					<text class="time" v-if="obj[vm.time]"><text>{{obj[vm.time]}}</text></text>
					<text class="address" v-if="obj[vm.address]"><text>{{obj[vm.address]}}</text></text>
					<text class="business" v-if="obj[vm.business]"><text>{{obj[vm.business]}}</text></text>
				</view>
			</view>
		</view>
	</mm_item>
</template>

<script>
	import mixin from '@/mixins/item.js'

	export default {
		mixins: [mixin],
		data() { return {};}
	}
</script>

<style>
</style>
