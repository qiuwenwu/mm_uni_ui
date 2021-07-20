<template>
	<!-- 音乐 -->
	<mm_item :url="obj[vm.url]">
		<view class="item_music" :class="css">
			<view class="media" v-if="display == 2">
				<mm_icon :src="obj[vm.image]" :desc="obj[vm.tip]"></mm_icon>
			</view>
			<view class="doc">
				<view class="collect"><text>{{obj[vm.collect]}}</text></view>
				<view class="name" v-if="obj[vm.name]"><text>{{obj[vm.name]}}</text></view>
				<view class="label" v-if="obj[vm.label]"><text>{{obj[vm.label]}}</text></view>
				<view class="tag" v-if="obj[vm.tag]"><text>{{obj[vm.tag]}}</text></view>
				<view class="time" v-if="obj[vm.time]"><text>{{obj[vm.time]}}</text></view>
				<view class="author" v-if="obj[vm.author]"><text>{{obj[vm.author]}}</text></view>
			</view>
		</view>
	</mm_item>
</template>

<script>
	import mixin from '@/mixins/item.js'

	export default {
		mixins: [mixin],
		props: {
			uid: {
				type: Number,
				default: 0
			}
		},
		methods: {
			click_fun(o) {
				var u = obj[this.vm.url];
				if (this.func) {
					if (!this.func(o)) {
						return;
					}
				}
				if (u) {
					this.$nav(u);
				}
			},
			has_collect(arr) {
				if (arr) {
					if (this.uid && arr) {
						return arr.has(this.field, this.uid);
					}
				}
				return false;
			}
		}
	}
</script>

<style>
	
</style>
