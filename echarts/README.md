## 学习echarts

### echarts是什么？

ECharts，一个使用 JavaScript 实现的开源可视化库，可以流畅的运行在 PC 和移动设备上，兼容当前绝大部分浏览器（IE8/9/10/11，Chrome，Firefox，Safari等），底层依赖轻量级的矢量图形库 ZRender，提供直观，交互丰富，可高度个性化定制的数据可视化图表。


### 如何在vue中引用echarts？

用vue脚手架搭建项目后，
    
            yarn add echarts

**在main.js中引用**

            import echarts from 'echarts'
            Vue.prototype.$echarts = echarts 

**在app.vue中**

            <div id="myChart" :style="{width: '300px', height: '300px'}"></div>
            <!-- 为 ECharts 准备一个具备大小（宽高）的 DOM -->


**在<script>中**

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
                     基于准备好的dom，初始化echarts实例
                    let myChart = this.$echarts.init(document.getElementById('myChart'))
                     绘制图表
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
