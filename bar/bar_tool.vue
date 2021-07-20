<template>
  <view class="bar_tool">
    <view class="list">
      <view class="item" v-for="(o, i) in list" :key="i">
        <view class="dropdown" :class="{show:index===i}">
          <!-- 一级 -->
          <view class="btn_first" @click="click_first(o,i)">
            <i :class="o[vm.icon]"></i>
            <text class="title">{{ o[vm.title] }}</text>
          </view>
          <!-- 二级 -->
          <view class="box" v-if="o[vm.sub] && o[vm.sub].length">
            <view class="dropdown_menu">
              <view class="btn_dropdown_item" v-for="(obj, idx) in o.sub" :key="idx" @click="click_second(obj, idx)">
                <i :class="obj[vm.icon]"></i>
                <text>{{ obj[vm.title] }}</text>
              </view>
            </view>
          </view>
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
              title: "百日誓师",
              command: "#",
              icon:"fa-bars",
              sub: [{
                  title: "高考真题",
                  command: "#",
                  icon:"fa-book"
                },
                {
                  title: "模拟试题",
                  command: "#",
                },
                {
                  title: "最新讲座",
                  command: "#",
                },
              ],
            },
            {
              title: "四六级",
              command: "#",
              icon:"fa-bars",
              sub: [{
                  title: "四六级真题",
                  command: "#",
                  icon:"fa-book"
                },
                {
                  title: "四六级真题",
                  command: "#",
                },
              ],
            },
            {
              title: "首页",
              command: "#",
            },
          ];
        },
      },
    },
    data() {
      return {
        index: -1
      }
    },
    methods: {
      // 点击一级
      click_first(o, i) {
        this.show_dropdown(i)
        this.event_click(o)
      },
      // 点击二级
      click_second(o, i) {
        this.close_dropdown()
        this.event_click(o)
      },
      // 展示下拉框
      show_dropdown(i) {
        let index = this.index
        if (index === i) {
          this.index = -1
        } else {
          this.index = i
        }
      },
      // 关闭下拉框
      close_dropdown(){
        this.index = -1
      },
      // 发射
      event_click(o) {
        if (this.func) {
          this.func(o);
        }
      }
    }
  };
</script>

<style scoped>

</style>
