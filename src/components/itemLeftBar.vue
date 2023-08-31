<script setup>
import { ref, onMounted } from 'vue'
import * as echarts from 'echarts'

// // 1实例化对象
const leftBar = ref()
onMounted(() => {
  let myChart = echarts.init(leftBar.value)
  // 2 指定配置项和数据
  let option = {
    color: ['#2f89cf'],
    tooltip: {
      trigger: 'axis',
      axisPointer: {
        type: 'shadow'
      }
    },
    grid: {
      left: '10%',
      top: '10px',
      right: '0%',
      bottom: '10%',
      containLabe: true
    },
    xAxis: {
      type: 'category',
      data: [
        '旅游行业',
        '教育培训',
        '游戏行业',
        '医疗行业',
        '电商行业',
        '社交行业',
        '金融行业'
      ],
      //保证刻度线和标签对齐。
      axisTick: {
        alignWithLabel: true,
        lineStyle: { color: 'rgba(255,255,255,0.3)' }
      },
      // 修改刻度标签相关样式
      axisLabel: {
        color: 'rgba(255,255,255,.6)',
        fontSize: '12'
      },
      // 不显示x坐标轴的样式
      axisLine: {
        show: false
      }
    },
    yAxis: {
      type: 'value',
      axisLabel: {
        color: 'rgba(255,255,255,.6)',
        fontSize: '12'
      },
      // y轴线条改为2像素
      axisLine: {
        lineStyle: {
          color: 'rgba(255,255,255,.1)',
          width: 2
        }
      },
      // y轴分割线的颜色
      splitLine: {
        lineStyle: {
          color: 'rgba(255,255,255,.1)'
        }
      }
    },
    series: [
      {
        name: '就业人数',
        data: [200, 300, 300, 900, 1500, 1200, 900],
        type: 'bar',
        barWidth: '35%',
        itemStyle: {
          //修改柱子圆角
          borderRadius: 5
        }
      }
    ]
  }
  //   3 把配置项给实例对象
  myChart.setOption(option)
  // 4 图标跟随屏幕自适应
  window.addEventListener('resize', function () {
    myChart.resize()
  })
})
</script>

<template>
  <div class="panel bar">
    <h2>柱状图-就业行业</h2>
    <div class="chart" ref="leftBar"></div>
    <div class="panel-footer"></div>
  </div>
</template>

<style lang="less" scoped></style>
