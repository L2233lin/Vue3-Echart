<script setup>
import { ref, onMounted } from 'vue'
import * as echarts from 'echarts'

// // 1实例化对象
const leftPie = ref()
onMounted(() => {
  let myChart = echarts.init(leftPie.value)
  // 2 指定配置项和数据
  let option = {
    tooltip: {
      trigger: 'item'
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
        name: '年龄分布',
        type: 'pie',
        radius: ['45%', '60%'], // [内圆半径，外圆半径]
        center: ['50%', '40%'],
        itemStyle: {
          borderRadius: 5,
          borderWidth: 2
        },
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
        labelLine: {
          show: true
        },
        data: [
          { value: 1, name: '20岁以下' },
          { value: 4, name: '20-29岁' },
          { value: 2, name: '30-39岁' },
          { value: 2, name: '40-49岁' },
          { value: 1, name: '50岁以上' }
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
    <h2>饼图-年龄分布</h2>
    <div class="chart" ref="leftPie"></div>
    <div class="panel-footer"></div>
  </div>
</template>

<style lang="less" scoped></style>
