<template>
    <div id="height-chart"></div>
  </template>
  
  <script>
 import * as echarts from 'echarts';
  
  export default {
    props: {
      heightData: {
        type: Array,
        required: true
      }
    },
    watch: {
      heightData: {
        immediate: true,
        handler(newVal) {
          if (newVal && newVal.length) {
            this.initChart();
          }
        }
      }
    },
    methods: {
      initChart() {
        this.$nextTick(() => {
          let chart = echarts.init(document.getElementById('height-chart'));
          // 这里可以配置 Echarts 图表的相关参数
          let option = {
            title: {
              text: '班级身高统计'
            },
            xAxis: {
              type: 'category',
              data: ['学生1', '学生2', '学生3', '学生4', '学生5']
            },
            yAxis: {
              type: 'value'
            },
            series: [
              {
                data: this.heightData,
                type: 'bar'
              }
            ]
          };
          chart.setOption(option);
        });
      }
    }
  };
  </script>
  
  <style>
  #height-chart {
    width: 600px;
    height: 400px;
  }
  </style>