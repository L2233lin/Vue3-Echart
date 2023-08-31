<script setup>
import { ref, onMounted } from 'vue'
import * as echarts from 'echarts'

// // 1实例化对象
const rightBar = ref()
onMounted(() => {
  let myChart = echarts.init(rightBar.value)
  let myColor = ['#1089E7', '#F57474', '#56D0E3', '#F8B448', '#8B78F6']
  // 2 指定配置项和数据
  let option = {
    grid: {
      top: '10%',
      left: '22%',
      bottom: '10%'
      // containLabel: true
    },
    // 不显示x轴的相关信息
    xAxis: {
      show: false
    },
    yAxis: [
      {
        type: 'category',
        inverse: true, //是否是反向坐标轴。
        data: ['HTMLS', 'CSS3', 'javascript', 'VUE', 'NODE'],
        // 不显示y轴的线
        axisLine: {
          show: false
        },
        // 不显示y轴刻度
        axisTick: {
          show: false
        },
        // 把刻度标签里面的文字颜色设置为白色
        axisLabel: {
          color: '#fff'
        }
      },
      {
        show: true,
        //type: 'category',
        inverse: true,
        data: [702, 680, 540, 320, 450],
        // 不显示y轴的线
        axisLine: {
          show: false
        },
        // 不显示y轴刻度
        axisTick: {
          show: false
        },
        // 把刻度标签里面的文字颜色设置为白色
        axisLabel: {
          color: '#fff'
        }
      }
    ],
    series: [
      {
        name: '条',
        type: 'bar',
        data: [70, 68, 54, 32, 45],
        yAxisIndex: 0,
        // 修改第一组柱子的圆角
        itemStyle: {
          borderRadius: 20,
          // 此时的color可以修改柱子的颜色
          color: function (params) {
            // params 传进来的是柱子对象
            return myColor[params.dataIndex]
          }
        },
        // 修改柱子之间的距离
        barCategoryGap: 50,
        //柱子的宽度
        barWidth: 10,
        // 显示柱子内的文字
        label: {
          show: true,
          position: 'inside',
          // {c}会自动解析为data数据
          formatter: '{c}%'
        }
      },
      {
        name: '框',
        type: 'bar',
        data: [100, 100, 100, 100, 100],
        yAxisIndex: 1,
        barCategoryGap: 50,
        barWidth: 15,
        itemStyle: {
          color: 'none',
          borderColor: '#00c1de',
          borderWidth: 3,
          borderRadius: 15
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
    <h2>柱状图-技能掌握</h2>
    <div class="chart" ref="rightBar"></div>
    <div class="panel-footer"></div>
  </div>
</template>

<style lang="less" scoped></style>
