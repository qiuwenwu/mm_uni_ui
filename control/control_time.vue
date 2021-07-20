<template>
	<view class="control_time">
		<view class="title" v-if="title" v-html="title"></view>
		<view class="value" v-bind:class="{'disabled': disabled }"><input :type="type || 'datetime'" :value="value" @blur="set"
			 :disabled="disabled"></select></view>
		<view class="tip" v-if="tip">{{ tip }}</view>
	</view>
</template>

<script>
	import mixin from "@/mixins/control.js";
	export default {
		mixins: [mixin],
		methods: {
			set(e) {
				this.$emit("input", e.target.value);
			}
		},
		watch: {
			value(e) {
				if (this.type === 'date') {
					this.$emit("input", new Date(this.value).toStr('yyyy-MM-dd'));
				} else if (this.type === 'datetime-local') {
					this.$emit("input", new Date(this.value).toStr('yyyy-MM-ddThh:mm:ss'));
				} else if (this.value.indexOf('Z') !== -1) {
					this.$emit("input", new Date(this.value).toStr('yyyy-MM-ddThh:mm'));
				}
			}
		}
	};
</script>

<style>
</style>
