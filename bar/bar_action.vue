<template>
  <!-- 操作栏 -->
  <view class="bar_action">
    <view class="btn_action" v-for="(o,i) in list" :key="i" @click="event_click(o)">{{o.title}}</view>
    <view class="btn_close" @click="event_click(obj_cancel)">{{obj_cancel.title}}</view>
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
              title: "拍照",
              command: "take_picture"
            },
            {
              title: "选取",
              command: "select"
            }
          ]
        },
      },
      obj_cancel: {
        type: Object,
        default () {
          return {
            title: "取消",
            command: "cancel"
          }
        }
      }
    },
    data() {
      return {};
    },
    methods: {
      event_click(o) {
        if (this.func) {
          this.func(o);
        }
      }
    },
  };
</script>

<style scoped>
</style>
