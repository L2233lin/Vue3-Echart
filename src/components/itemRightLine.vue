<script setup>
import { ref, onMounted } from 'vue'
import * as echarts from 'echarts'

// // 1实例化对象
const rightLine = ref()
onMounted(() => {
  let myChart = echarts.init(rightLine.value)
  // 2 指定配置项和数据
  let option = {
    tooltip: {
      trigger: 'axis'
    },
    legend: {
      right: '10%',
      data: ['Union Ads', 'Video Ads'],
      textStyle: {
        color: 'rgba(255,255,255,.5',
        fontSize: '12'
      }
    },
    grid: {
      left: '10',
      top: '30',
      right: '10',
      bottom: '10',
      containLabel: true
    },
    xAxis: [
      {
        type: 'category',
        boundaryGap: false,
        data: [
          '01',
          '02',
          '03',
          '04',
          '05',
          '06',
          '07',
          '08',
          '09',
          '10',
          '11',
          '12',
          '13',
          '14',
          '15',
          '16',
          '17',
          '18',
          '19',
          '20',
          '21',
          '22',
          '23',
          '24',
          '25',
          '26',
          '27',
          '28',
          '29',
          '30'
        ],
        textStyle: {
          color: 'rgba(255,255,255,.6)',
          fontSize: 12
        },
        axisLine: {
          lineStyle: {
            color: 'rgba(255,255,255,.2)'
          }
        }
      }
    ],
    yAxis: [
      {
        type: 'value',
        axisTickL: { show: false },
        textStyle: {
          color: 'rgba(255,255,255,.6)',
          fontSize: 12
        },
        axisLine: {
          lineStyle: {
            color: 'rgba(255,255,255,.2)'
          }
        },
        splitLine: {
          lineStyle: {
            color: 'rgba(255,255,255,.1)'
          }
        }
      }
    ],
    series: [
      {
        name: 'Video Ads',
        type: 'line',
        smooth: true,
        lineStyle: {
          color: '#0184d5',
          width: '3'
        },
        // 填充颜色
        areaStyle: {
          //渐变色
          color: {
            type: 'linear',
            x: 0,
            y: 0,
            x2: 0,
            y2: 1,
            colorStops: [
              {
                offset: 0,
                color: 'rgba(1, 132, 213, 0.4)' // 0% 处的颜色
              },
              {
                offset: 1,
                color: 'rgba(1, 132, 213, 0.1)' // 100% 处的颜色
              }
            ],
            global: false // 缺省为 false
          },
          shadowColor: 'rgba(0, 0, 0, 0.1)'
        },
        // 设置拐点
        symbol: 'circle',
        // 拐点大小
        symbolSize: 8,
        showSymbol: false, // 如果 false 则只有在 tooltip hover 的时候显示。
        itemStyle: {
          color: '#0184d5',
          borderColor: 'rgba(221, 220, 107, .1)',
          borderWidth: 12
        },
        data: [
          30, 40, 30, 40, 30, 40, 30, 60, 20, 40, 30, 40, 30, 40, 30, 40, 30,
          60, 20, 40, 30, 40, 30, 40, 30, 40, 20, 60, 50, 40
        ]
      },
      {
        name: 'Union Ads',
        type: 'line',
        smooth: true,
        lineStyle: {
          color: '#00d887',
          width: '3'
        },
        // 填充颜色
        areaStyle: {
          color: {
            type: 'linear',
            x: 0,
            y: 0,
            x2: 0,
            y2: 1,
            colorStops: [
              {
                offset: 0,
                color: 'rgba(0, 216, 135, 0.4)' // 0% 处的颜色
              },
              {
                offset: 1,
                color: 'rgba(0, 216, 135, 0.1)' // 100% 处的颜色
              }
            ],
            global: false // 缺省为 false
          },
          shadowColor: 'rgba(0, 0, 0, 0.1)'
        },
        // 设置拐点
        symbol: 'circle',
        // 拐点大小
        symbolSize: 5,
        showSymbol: false,
        itemStyle: {
          color: '#00d887',
          borderColor: 'rgba(221, 220, 107, .1)',
          borderWidth: 12
        },
        data: [
          130, 10, 20, 40, 30, 40, 80, 60, 20, 40, 90, 40, 20, 140, 30, 40, 130,
          20, 20, 40, 80, 70, 30, 40, 30, 120, 20, 99, 50, 20
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
    <h2>折线图-播放量变化</h2>
    <div class="chart" ref="rightLine"></div>
    <div class="panel-footer"></div>
  </div>
</template>

<style lang="less" scoped></style>
