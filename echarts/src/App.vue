<template>
<div id="myChart" :style="{width: '300px', height: '300px'}"></div>
</template>

<script>
import HelloWorld from './components/HelloWorld'

export default {
  name: 'hello',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App'
    }
  },
  mounted(){
    this.drawLine();
  },
  methods: {
    drawLine(){
        // 基于准备好的dom，初始化echarts实例
        let myChart = this.$echarts.init(document.getElementById('myChart'))
        // 绘制图表
        myChart.setOption({
            title: { text: '京东双十一手机销量环形图' },
            tooltip: {
              trigger: 'item',
              formatter: "{a} <br/>{b}: {c} ({d}%)"
            },
    series: [
        {
            name:'手机品牌',
            type:'pie',
            radius: ['50%', '70%'],
            avoidLabelOverlap: false,
            label: {
                normal: {
                    show: false,
                    position: 'center'
                },
                emphasis: {
                    show: true,
                    textStyle: {
                        fontSize: '30',
                        fontWeight: 'bold'
                    }
                }
            },
            labelLine: {
                normal: {
                    show: false
                }
            },
            data:[
                {value:800, name:'华为'},
                {value:500, name:'OPPO'},
                {value:300, name:'vivo'},
                {value:135, name:'魅族'},
                {value:1200, name:'小米'},
                {value:700, name:'苹果'}
            ]
        }
    ]
        });
    }
  }
}
</script>

<style>

</style>
