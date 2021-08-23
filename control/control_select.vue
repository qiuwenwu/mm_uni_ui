<template>
	<view class="control_select">
		<view class="title" v-if="title" v-html="title"></view>
		<view class="value" v-bind:class="{'disabled': disabled }">
			<picker :value="v" :range="options" :range-key="rangeKey" @change="set">
				<label>{{ options[index].name }}</label>
			</picker>
		</view>
		<view class="tip" v-if="tip">{{ tip }}</view>
	</view>
</template>

<script>
	import mixin from "@/mixins/control.js";
	export default {
		mixins: [mixin],
		props: {
			rangeKey: {
				type: String,
				default: "value"
			}
		},
		methods: {
			set: function set(e) {
				var value = e.target.value;
				this.$emit("input", value);
				if (this.value !== value) {
					this.$emit("change");
				}
			},
			click_fun: function click_fun(value) {
				this.$emit("input", value);
				this.func(value);
			}
		},
		computed: {
			val_name: function val_name() {
				var k = this.field;
				var v = this.value;
				var lt = this.options;
				var name = "";

				for (var i = 0; i < lt.length; i++) {
					var o = lt[i];

					if (o[k] === v) {
						name = o.name;
						break;
					}
				}

				return name;
			}
		}
	};
</script>

<style>
</style>
