<template>
	<!-- 商品 -->
	<mm_item :url="obj[vm.url]">
		<view class="item_goods" :class="css">
			<view class="media">
				<mm_icon :src="obj[vm.image]" :desc="obj[vm.tip]"></mm_icon>
				<text class="tag" v-if="obj[vm.tag]"><text>{{obj[vm.tag]}}</text></text>
			</view>
			<view class="doc">
				<view class="title" v-if="obj[vm.title]"><text>{{obj[vm.title]}}</text></view>
				<view class="content" v-if="obj[vm.description]"><text>{{obj[vm.description]}}</text></view>
				<view class="price" v-if="obj[vm.price]"><text>{{obj[vm.price]}}</text></view>
				<view class="price_ago" v-if="obj[vm.price_ago]"><text>{{obj[vm.price_ago]}}</text></view>
				<view class="num_comment"><text>{{obj[vm.num_comment]}}</text></view>
				<view class="collect"><text>{{obj[vm.collect]}}</text></view>
				<view class="info">
					<view class="freight" v-if="(obj[vm.freight] && obj[vm.freight] > 0)"><text class="freight_before">{{obj[vm.freight]}}</text></view>
					<view class="freight" v-else><text>免运费</text></view>
					<view class="address" v-if="obj[vm.address]">
						<text>{{obj[vm.address]}}</text>
					</view>
					<view class="hot"><text>{{obj[vm.hot]}}</text></view>
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
