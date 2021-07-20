<template>
	<view class="control_textarea" :class="{ 'show-expand': sw }">
		<view class="title" v-if="title" v-html="title"></view>
		<view class="value" v-bind:class="{'disabled': disabled }"><textarea :value="value" @blur="set" :disabled="disabled"
			 :placeholder="desc || placeholder" v-if="type == 'text'"></textarea><button class="btn_expand" type="button" v-show="$slots.default"
			 @click="sw = !sw"><i class="fa-expand"></i></button></view>
		<view class="tip" v-if="tip">{{ tip }}</view>
		<slot></slot>
	</view>
</template>

<script>
	import mixin from "@/mixins/control.js";

	export default {
		mixins: [mixin],
		props: {
			placeholder: {
				type: String
			}
		},
		methods: {
			set: function set(e) {
				this.$emit("input", e.target.value);
			}
		}
	};
</script>

<style>
</style>
