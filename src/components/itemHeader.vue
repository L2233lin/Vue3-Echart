<script setup>
import { ref, onMounted, onUnmounted } from 'vue'
import { formatTime } from '@/utils/dateFormat.js'

const timer = ref()
const showTime = ref()

const setTime = () => {
  clearTimeout(timer) //清除定时器
  showTime.value.innerHTML = formatTime(new Date())
  timer.value = setTimeout(setTime, 1000) //循环运行
}

onMounted(() => {
  setTime() //开启定时器
})

onUnmounted(() => {
  clearTimeout(timer)
})
</script>

<template>
  <header>
    <div class="showTime" ref="showTime">123</div>
    <h1>数据可视化-ECharts</h1>
    <div class="author">by LYG</div>
  </header>
</template>

<style lang="less" scoped>
header {
  position: relative;
  height: 100%;
  background: url(@/assets/head_bg.png) no-repeat;
  background-size: 100% 100%;

  .showTime {
    position: absolute;
    left: 1.5vw;
    top: 0;
    line-height: 3.75vw;
    color: rgba(255, 255, 255, 0.7);
    font-size: 1vw;
  }

  h1 {
    font-size: 2vw;
    color: #fff;
    text-align: center;
    line-height: 4vw;
  }

  .author {
    position: absolute;
    right: 1.5vw;
    top: 0;
    line-height: 3.75vw;
    color: rgba(255, 255, 255, 0.7);
    font-size: 1vw;
  }
}
</style>
