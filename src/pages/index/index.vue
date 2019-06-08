<template>
  <div class="app">
    <div>{{name}}</div>
    <ul>
      <li v-for="item in list" :key="item">{{item}}</li>
    </ul>
    <div>{{count}}</div>
    <button @click="increment">点击</button>
    <picker mode="date" :value="date" start="2015-09-01" end="2017-09-01" @change="bindDateChange">
      <view class="picker">当前选择: {{date}}</view>
    </picker>
    <button class="btn" @click="navTo">跳转到log</button>
  </div>
</template>

<script>
import card from '@/components/card'
import { toTabPage } from '@/utils/index'
export default {
  data () {
    return {
      count: 0,
      name: 'wnf',
      list: ['a', 'b', 'c']
    }
  },

  components: {
    card
  },

  methods: {
    increment () {
      this.count++
    },
    bindDateChange (data) {
      console.log(data.mp.detail.value)
      this.data = data.mp.detail.value
    },
    navTo () {
      toTabPage('../logs/main')
    }
  },

  created () {
    // let app = getApp()
  }
}
</script>

<style scoped lang='scss'>
.app {
  background: #999;
  .btn {
    width: 300rpx;
  }
}
</style>
