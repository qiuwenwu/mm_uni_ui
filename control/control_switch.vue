<template>
	<view class="control_switch">
		<view class="title" v-if="title" v-html="title"></view>
		<view class="value" v-bind:class="{'disabled': disabled }"><label :class="{ 'active': value === 1 }" @click="set">
				<view class="onoff"><text class="on" v-if="display === '1'"></text><text class="off" v-if="display === '1'"></text></view>
			</label></view>
		<view class="tip" v-if="tip">{{ tip }}</view>
	</view>
</template>

<script>
	import mixin from "@/mixins/control.js";
	export default {
		mixins: [mixin],
		methods: {
			set: function set() {
				var val = 0;

				if (this.value === 0) {
					val = 1;
				}

				this.$emit("input", val);
			}
		}
	};
</script>

<style>
</style>
