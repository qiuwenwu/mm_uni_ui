<template>
	<view class="nav_menu">
		<mm_list>
			<mm_item v-for="(o, i) in list" :url="o[vm.url]">
				<view class="item_menu">
					<mm_icon v-if="o[vm.img]" :src="o[vm.img]"></mm_icon>
					<text class="title" v-if="show_title && o[vm.title]">{{ o[vm.title] }}</text>
				</view>
			</mm_item>
		</mm_list>
	</view>
</template>

<script>
	export default {
		data() {
			return {
			}
		}
	}
	// import mixin from '@/mixins/component.js'

	// export default {
	// 	mixins: [mixin],
	// 	onLoad(){
	// 	}
	// }
</script>

<style>
</style>
