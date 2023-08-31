<script setup>
import { ref, onMounted, watch } from 'vue'
import * as echarts from 'echarts'
//请避免使用 reactive 及 ref 实例化echart对象。
//否则将导致 ECharts 的对象实例被代理成为响应式对象
//影响 ECharts 对内部属性的访问
//可能会导致图表无法正确显示等一系列意外问题
//且会由于深度监听而极大地降低图表展示性能。
let myChart
const leftLine = ref()
const yearData = ref([
  {
    year: '2021',
    data: [
      [24, 40, 101, 134, 90, 230, 210, 230, 120, 230, 210, 120],
      [40, 64, 191, 324, 290, 330, 310, 213, 180, 200, 180, 79]
    ]
  },
  {
    year: '2022',
    data: [
      [123, 175, 112, 197, 121, 67, 98, 21, 43, 64, 76, 38],
      [143, 131, 165, 123, 178, 21, 82, 64, 43, 60, 19, 34]
    ]
  }
])
const data = ref()
const radio1 = ref('1')

onMounted(() => {
  // // 1实例化对象
  myChart = echarts.init(leftLine.value)
  data.value = yearData.value[0]
  setEchart()
})

const setEchart = () => {
  // 2 指定配置项和数据
  let option = {
    tooltip: {
      show: true,
      trigger: 'axis'
    },
    legend: {
      data: ['新增粉丝', '新增游客'],
      textStyle: {
        color: '#4c9bfd'
      },
      right: '10%'
    },
    grid: {
      top: '20%',
      left: '3%',
      right: '4%',
      bottom: '3%',
      show: true, //显示边框
      borderColor: '#012f4a', //边框颜色
      containLabel: true
    },
    xAxis: {
      type: 'category',
      boundaryGap: false,
      data: [
        '1月',
        '2月',
        '3月',
        '4月',
        '5月',
        '6月',
        '7月',
        '8月',
        '9月',
        '10月',
        '11月',
        '12月'
      ],
      axisTick: {
        show: false // 去除刻度线
      },
      axisLabel: {
        color: '#4c9bfd' // 文本颜色
      },
      axisLine: {
        show: false //去除轴线
      }
    },
    yAxis: {
      type: 'value',
      axisTick: {
        show: false // 去除刻度线
      },
      axisLabel: {
        color: '#4c9bfd' // 文本颜色
      },
      axisLine: {
        show: false //去除轴线
      },
      splitLine: {
        lineStyle: {
          color: '#012f4a'
        }
      }
    },
    series: [
      {
        name: '新增粉丝',
        type: 'line',
        data: data.value.data[0],
        smooth: true
      },
      {
        name: '新增游客',
        type: 'line',
        data: data.value.data[1],
        smooth: true
      }
    ]
  }
  //   3 把配置项给实例对象
  myChart.setOption(option)
  // 4 图标跟随屏幕自适应
  window.addEventListener('resize', function () {
    myChart.resize()
  })
}

watch(radio1, (newValue) => {
  if (newValue === '2') {
    data.value = yearData.value[1]
    setEchart()
  } else {
    data.value = yearData.value[0]
    setEchart()
  }
})
</script>

<template>
  <div class="panel line">
    <h2>
      折线图-人员变化
      <el-radio-group v-model="radio1" class="ml-4">
        <el-radio label="1" size="large">2021</el-radio>
        <el-radio label="2" size="large">2022</el-radio>
      </el-radio-group>
    </h2>
    <div class="chart" ref="leftLine"></div>
    <div class="panel-footer"></div>
  </div>
</template>

<style lang="less" scoped></style>
