<template>
	<!-- 消息 -->
	<mm_item :url="obj[vm.url]">
		<view class="item_message" :class="css">
			<view class="media">
				<mm_icon :src="obj[vm.avatar]" :desc="obj[vm.tip]"></mm_icon>
				<view class="num_message" :class="{'point':obj[vm.type] !== 1}" v-if="obj[vm.num_message]"><text class="text">{{obj[vm.num_message]}}</text></view>
			</view>
			<view class="doc">
				<view class="name" v-if="obj[vm.name]"><text>{{obj[vm.name]}}</text></view>
				<view class="content" v-if="obj[vm.content]"><text>{{obj[vm.content]}}</text></view>
				<view class="time" v-if="obj[vm.create_time]"><text>{{ $to_time(obj[vm.create_time]) }}</text></view>
				<view class="mute" v-if="obj[vm.mute]"><text>{{obj[vm.mute]}}</text></view>
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
