<template>
  <view class="control_radio">
    <view class="title" v-if="title" v-html="title"></view>
    <view class="value" v-bind:class="{'disabled': disabled }">
      <label v-for="(o, idx) in options" :key="idx" :class="{ 'active': value == o[field] }"
        @click="$emit('input', $event.target.value)">
        <slot :row="o"><text class="figure"></text><text class="name" @click="o[field]">{{ o.name }}</text></slot>
      </label>
    </view>
    <view class="tip" v-if="tip">{{ tip }}</view>
  </view>
</template>

<script>
  import mixin from "@/mixins/control.js";
  export default {
    mixins: [mixin],
    data: function data() {
      var name = this.name;

      if (!name) {
        name = uni.md5(Math.random().toString()).substring(0, 8);
      }

      return {
        name: name
      };
    }
  };
</script>

<style>
</style>
