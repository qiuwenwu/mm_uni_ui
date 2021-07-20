<template>
	<view class="bar_menu">
		<view class="list">
			<view @click="event_click(o)" class="item" v-for="(o, i) in list" :key="i">
					<view class="media">
						<mm_icon :src="o[vm.img]"></mm_icon>
					</view>
					<view class="title">
            <text>{{ o[vm.title] }}</text>
					</view>
			</view>
		</view>
	</view>
</template>

<script>
	import mixin from '@/mixins/component.js'
	export default {
		mixins: [mixin],
		props: {
			list: {
				type: Array,
				default () {
					return [{
							title: "手机充值",
							img: "/img/default.png",
							url:"#"
						},
						{
							title: "生活",
							img: "/img/default.png",
							url:"#"
						},
						{
							title: "Q币充值",
							img: "/img/default.png",
							url:"#"
						},
						{
							title: "城市服务",
							img: "/img/default.png",
							url:"#"
						},
						{
							title: "腾讯公益",
							img: "/img/default.png",
							url:"#"
						},
					];
				},
			},
		},
		methods: {
      // 发射事件
      event_click(o) {
      	if (this.func) {
      		this.func(o);
      	}
      },
		},
		components: {},
	};
</script>

<style scoped>

</style>
