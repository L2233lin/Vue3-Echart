<script setup>
import { ref, onMounted } from 'vue'
import * as echarts from 'echarts'

// // 1实例化对象
const rightPie = ref()
onMounted(() => {
  let myChart = echarts.init(rightPie.value)
  // 2 指定配置项和数据
  let option = {
    color: [
      '#006cff',
      '#60cda0',
      '#ed8884',
      '#ff9f7f',
      '#0096ff',
      '#9fe6b8',
      '#32c5e9',
      '#1d9dff'
    ],
    tooltip: {
      trigger: 'item',
      formatter: '{a} <br/>{b} : {c} ({d}%)'
    },
    legend: {
      bottom: '0%',
      itemWidth: 10,
      itemHeight: 10,
      textStyle: {
        color: 'rgba(255,255,255,.5)',
        fontSize: '12'
      }
    },
    series: [
      {
        name: '地区分布',
        type: 'pie',
        radius: ['10%', '70%'],
        center: ['50%', '40%'],
        roseType: 'radius',
        // 图形的文字标签
        label: {
          show: true,
          position: 'outside',
          color: 'inherit'
        },
        emphasis: {
          label: {
            show: true,
            fontSize: 20,
            fontWeight: 'bold'
          }
        },
        //连接图形和文字的线条
        labelLine: {
          // 连接图形的线条
          length: 6,
          // 连接欸文字的线条
          length2: 8
        },
        itemStyle: {
          borderRadius: 5
        },
        data: [
          { value: 20, name: '云南' },
          { value: 26, name: '北京' },
          { value: 24, name: '山东' },
          { value: 25, name: '河北' },
          { value: 20, name: '江苏' },
          { value: 25, name: '浙江' },
          { value: 30, name: '四川' },
          { value: 42, name: '湖北' }
        ]
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
    <h2>饼图-地区分布</h2>
    <div class="chart" ref="rightPie"></div>
    <div class="panel-footer"></div>
  </div>
</template>

<style lang="less" scoped></style>
