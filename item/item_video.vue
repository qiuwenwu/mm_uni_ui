<template>
	<!-- 视频 -->
	<mm_item :url="obj[vm.url]">
		<view class="item_video" :class="css">
			<view class="media">
				<mm_icon :src="obj[vm.image]" :desc="obj[vm.tip]"></mm_icon>
				<text class="label" v-if="obj[vm.label]"><text>{{obj[vm.label]}}</text></text>
				<text class="tag" v-if="obj[vm.tag]"><text>{{obj[vm.tag]}}</text></text>
				<text class="score" v-if="obj[vm.score]"><text>{{obj[vm.score]}}</text></text>
			</view>
			<view class="doc">
				<view class="name" v-if="obj[vm.name]"><text>{{obj[vm.name]}}</text></view>	
				<view class="content" v-if="obj[vm.description]"><text>{{obj[vm.description]}}</text></view>
				<view class="num_see" v-if="obj[vm.num_see]"><text>{{obj[vm.num_see]}}</text></view>
				<view class="num_comment" v-if="obj[vm.num_comment]"><text>{{obj[vm.num_comment]}}</text></view>
				<view class="time" v-if="obj[vm.time]"><text>{{obj[vm.time]}}</text></view>
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
