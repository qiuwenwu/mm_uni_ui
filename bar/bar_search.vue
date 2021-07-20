<template>
	<view class="bar_search">
		<view class="cancle" @click="even_click(obj.cancle)"><text>{{ obj.cancle.title }}</text></view>
		<view class="warp_search">
			<input class="input" type="text" :placeholder="desc" :value="value" v-on:input="$emit('input', $event.target.value)">
			<text class="btn_search" @click="even_click(obj.search)"></text>
		</view>
		<view class="box">
			<view v-for="(o,i) in list_keyword" :key="i" @click="$emit('change', o.keyword)">{{ o.keyword }}</view>
		</view>
	</view>
</template>

<script>
	import mixin from '@/mixins/control.js';
	
	export default {
		mixins: [mixin],
		model: {
			prop: 'value',
			event: 'input'
		},
		props: {
			value: {
				type: String,
				default: ""
			},
			obj: {
				type: Object,
				default () {
					return {
						search: {
							title: "搜索",
							command: "search"
						},
						cancle: {
							title: "取消",
							command: "cancle"
						}
					}
				}
			}
		},
		data() {
			return {
				list_keyword: []
			};
		},
		methods: {
			even_click(o) {
				if (this.func) {
					this.func(o);
				}
			}
		}
	}
</script>

<style>

</style>
