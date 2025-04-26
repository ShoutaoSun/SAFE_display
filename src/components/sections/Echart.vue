<script>
import { use } from 'echarts/core';
import { CanvasRenderer } from 'echarts/renderers';
import { BarChart, LineChart } from 'echarts/charts';
import {
  TitleComponent,
  TooltipComponent,
  LegendComponent,
  GridComponent,
  ToolboxComponent
} from 'echarts/components';
import VChart, { THEME_KEY } from 'vue-echarts';
import { provide } from 'vue';

use([
  CanvasRenderer,
  BarChart,
  LineChart,
  TitleComponent,
  TooltipComponent,
  LegendComponent,
  GridComponent,
  ToolboxComponent
]);

export default {
  components: {
    VChart,
  },
  setup() {
    provide('THEME_KEY', 'light');
  },
  data() {
    const labelOption = {
      show: true,
      position: 'insideBottom',
      distance: 22,
      align: 'left',
      verticalAlign: 'middle',
      rotate: 90,
      formatter: '{c}   {name|{a}}',
      fontSize: 16,
      rich: {
        name: {}
      }
    };
    
    return {
      barOption: {
        title: {
          text: '选取不同阈值区间样本时的攻击效果',
          left: 'center'
        },
        tooltip: {
          trigger: 'axis',
          axisPointer: {
            type: 'shadow'
          }
        },
        legend: {
          data: ['ResNet-18', 'VGG11', 'MobileNetV2'],
          left: 'center',
          top: 'bottom'
        },
        xAxis: [
          {
            type: 'category',
            axisTick: { show: false },
            data: [
              '[0.0, 0.2]',
              '[0.2, 0.4]',
              '[0.4, 0.6]',
              '[0.6, 0.8]',
              '[0.8, 1.0]'
            ]
          }
        ],
        yAxis: [
          {
            type: 'value',
            min: 50,
            max: 100
          }
        ],
        series: [
          {
            name: 'ResNet-18',
            type: 'bar',
            barGap: 0,
            label: labelOption,
            emphasis: {
              focus: 'series'
            },
            itemStyle: {
              color: '#5470c6'
            },
            data: [92.8, 90.8, 88.0, 84.6, 81.3]
          },
          {
            name: 'VGG11',
            type: 'bar',
            label: labelOption,
            emphasis: {
              focus: 'series'
            },
            itemStyle: {
              color: '#91cc75'
            },
            data: [94.2, 89.2, 85.6, 82.6, 78.3]
          },
          {
            name: 'MobileNetV2',
            type: 'bar',
            label: labelOption,
            emphasis: {
              focus: 'series'
            },
            itemStyle: {
              color: '#fac858'
            },
            data: [93.3, 88.9, 85.7, 82.9, 78.1]
          }
        ]
      },
      poisonRateOption: {
        title: {
          text: '扰动大小对攻击成功率的影响',
          left: 'center'
        },
        tooltip: {
          trigger: 'axis'
        },
        legend: {
          data: ['CIFAR-10', 'CIFAR-100', 'CelebA', 'Food-10'],
          top: 'bottom'
        },
        grid: {
          left: '10%',
          right: '7%',
          bottom: '8%',
          containLabel: true
        },
        xAxis: {
          type: 'category',
          axisTick: { show: false },
          data: ['4/255', '8/255', '10/255', '12/255', '16/255']
        },
        yAxis: {
          type: 'value',
          min: 0,
          max: 100
        },
        series: [
          {
            name: 'CIFAR-10',
            type: 'line',
            lineStyle: {
              width: 3
            },
            emphasis: {
              focus: 'series'
            },
            data: [12.0, 53.4, 74.4, 75.7, 93.1]
          },
          {
            name: 'CIFAR-100',
            type: 'line',
            lineStyle: {
              width: 3
            },
            emphasis: {
              focus: 'series'
            },
            data: [8.2, 52.3, 68.5, 76.8, 90.1]
          },
          {
            name: 'CelebA',
            type: 'line',
            lineStyle: {
              width: 3
            },
            emphasis: {
              focus: 'series'
            },
            data: [25.1, 60.7, 76.4, 82.6, 94.8]
          },
          {
            name: 'Food-10',
            type: 'line',
            emphasis: {
              focus: 'series'
            },
            lineStyle: {
              width: 3
            },
            data: [9.1, 45.9, 65.3, 72.5, 86.2]
          }
        ]
      },
      perturbationOption: {
        title: {
          text: '投毒率对攻击成功率的影响',
          left: 'center'
        },
        tooltip: {
          trigger: 'axis'
        },
        legend: {
          data: ['ResNet-18', 'VGG11', 'MobileNetV2'],
          top: 'bottom'
        },
        grid: {
          left: '10%',
          right: '7%',
          bottom: '8%',
          containLabel: true
        },
        xAxis: {
          type: 'category',
          axisTick: { show: false },
          data: ['0.0', '0.2', '0.4', '0.6', '0.8', '1.0']
        },
        yAxis: {
          type: 'value',
          min: 50,
          max: 100
        },
        series: [
          {
            name: 'ResNet-18',
            type: 'line',
            lineStyle: {
              width: 3
            },
            emphasis: {
              focus: 'series'
            },
            data: [73.1, 78.4, 88.3, 91.3, 92.0, 93.1]
          },
          {
            name: 'VGG11',
            type: 'line',
            lineStyle: {
              width: 3
            },
            emphasis: {
              focus: 'series'
            },
            data: [93.6, 95.7, 97.5, 97.8, 98.0, 98.9]
          },
          {
            name: 'MobileNetV2',
            type: 'line',
            lineStyle: {
              width: 3
            },
            emphasis: {
              focus: 'series'
            },
            data: [88.6, 93.4, 94.1, 95.4, 96.3, 96.7]
          }
        ]
      }
    }
  }
}
</script>

<template>
  <div>
    <el-divider />

    <el-row justify="center">
      <h1 class="section-title">Quantitative Results</h1>
    </el-row>

    <!-- 柱状图 -->
    <el-row justify="center">
      <el-col :xs="24" :sm="20" :md="16" :lg="12" :xl="12">
        <v-chart class="chart" :option="barOption" autoresize />
      </el-col>
    </el-row>

    <!-- 投毒率图表 -->
    <el-row justify="center" style="margin-top: 40px;">
      <el-col :xs="24" :sm="20" :md="16" :lg="12" :xl="12">
        <v-chart class="chart" :option="poisonRateOption" autoresize />
      </el-col>
    </el-row>

    <!-- 扰动大小图表 -->
    <el-row justify="center" style="margin-top: 40px;">
      <el-col :xs="24" :sm="20" :md="16" :lg="12" :xl="12">
        <v-chart class="chart" :option="perturbationOption" autoresize />
      </el-col>
    </el-row>
  </div>
</template>

<style scoped>
.chart {
  height: 400px;
  margin-top: 20px;
}
.section-title {
  margin: 20px 0;
}
</style>