<template>
  <div class="row">
    <div class="col-md-2" v-for="(node,index) in chartsTemp">
      <div class="panel panel-chart">
        <div class="panel-heading">
          <div class="panel-control"><i class="iconfont icon-bangzhu" data-toggle="tooltip" data-placement="bottom" :title="node.tooltipCont"></i></div>
          <h3 class="head-title">{{node.title}}</h3>
          <h1 class="head-cont">{{node.titCont}}</h1>
        </div>
        <div class="panel-body">
          <div v-if="index != 5" class="chartsbox" :id="forId(index)"></div>
          <div v-if="index == 5" class="progress">
            <div class="progress-bar bg-success" role="progressbar" :style="{width: node.titCont}" aria-valuenow="65" aria-valuemin="0" aria-valuemax="100"></div>
          </div>
        </div>
        <div class="panel-footer">
          <p class="footer-title">周环比 {{node.footTit}}</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>

  // 引入基本模板
  let echarts = require('echarts/lib/echarts');
  // 引入柱状图组件
  require('echarts/lib/chart/bar');
  require('echarts/lib/chart/line');
  // 引入提示框和title组件
  require('echarts/lib/component/tooltip');
  //引入主题
  require("echarts/theme/macarons");
  export default {
    name: 'Index',
    data () {
      return {
        msg: 'Welcome to Your Vue.js App',
        chartsTemp:[
          {
            title:'近七天所有事件',
            titCont:'100',
            tooltipCont:'下侧显示近30天事件变化趋势',
            option :{
              grid:{left:0, right:0, top:0, bottom:0},
              xAxis: {
                show : false,
                type: 'category',
                // data: ['Mon', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat', 'Sun']
              },
              yAxis: {
                show : false,
                type: 'value',
                // axisLine:{       //y轴
                //   "show":false
                // },
                // axisTick:{       //y轴刻度线
                //   "show":false
                // },
                // splitLine: {     //网格线
                //   "show": false
                // }
              },
              series: [{
                itemStyle: {
                  normal: {
                    color:'#91c7ae',
                    // 随机显示
                    // color:function(d){return "#"+Math.floor(Math.random()*(256*256*256-1)).toString(16);}

                    // 定制显示（按顺序）
                    // color: function(params) {
                    //   var colorList = ['#C33531','#EFE42A','#64BD3D','#EE9201','#29AAE3', '#B74AE5','#0AAF9F','#E89589','#16A085','#4A235A','#C39BD3 ','#F9E79F','#BA4A00','#ECF0F1','#616A6B','#EAF2F8','#4A235A','#3498DB' ];
                    //   return colorList[params.dataIndex]
                    // }
                  },
                },
                data: [160, 170, 191, 199, 200, 230, 210, 220, 242, 221, 240, 280, 300, 320, 410, 290, 298, 223, 275, 220,250, 230, 210, 223, 242, 201, 200, 190, 160, 150],
                type: 'bar'
              }]
            },
            footTit:'+12.12%'
          },
          {
            title:'近七天所有告警',
            titCont:'50',
            tooltipCont:'下侧显示近30天告警变化趋势',
            option :{
              grid:{left:0, right:0, top:0, bottom:0},
              xAxis: {
                show : false,
                type: 'category',
              },
              yAxis: {
                show:false,
                type: 'value'
              },
              series: [{
                itemStyle: {
                  normal: {
                    color:'pink',
                  },
                },
                data: [160, 170, 191, 199, 200, 230, 210, 220, 242, 221, 240, 280, 300, 320, 410, 290, 298, 223, 275, 220,250, 230, 210, 223, 242, 201, 200, 190, 160, 150],
                type: 'bar'
              }]
            },
            footTit:'+12.12%'
          },
          {
            title:'近七天所有聚类',
            titCont:'5',
            tooltipCont:'下侧显示近30天聚类变化趋势',
            option :{
              grid:{left:0, right:0, top:0, bottom:0},
              xAxis: {
                show:false,
                type: 'category',
              },
              yAxis: {
                show:false,
                type: 'value'
              },
              series: [{
                itemStyle: {
                  normal: {
                    color:'#ddbea0',
                  },
                },
                data: [160, 170, 191, 199, 200, 230, 210, 220, 242, 221, 240, 280, 300, 320, 410, 290, 298, 223, 275, 220,250, 230, 210, 223, 242, 201, 200, 190, 160, 150],
                type: 'bar'
              }]
            },
            footTit:'-12.12%'
          },
          {
            title:'近七天平均响应时长',
            titCont:'30min18s',
            tooltipCont:'MTTA：平均响应/认领时长\n下侧显示近30天MTTA变化趋势',
            option : {
              grid:{left:0, right:0, top:0, bottom:0},
              xAxis: {
                show:false,
                type: 'category',
                boundaryGap: false,
              },
              yAxis: {
                show:false,
                type: 'value'
              },
              series: [{
                symbol:'none',
                itemStyle: {
                  normal: {
                    color:'#469fdd',
                    borderColor:'green',  //拐点边框颜色
                  },
                },
                data: [80, 100, 70, 80, 120, 80, 100, 70, 80, 120,80, 100, 70, 80, 120, 80, 100, 70, 80, 120],
                type: 'line',
                areaStyle: {}
              }]
            },
            footTit:'+12.12%'
          },
          {
            title:'近七天平均处理时间',
            titCont:'32min13s',
            tooltipCont:'MTTR：平均处理/关闭时长\n下侧显示近30天MTTR变化趋势',
            option : {
              grid:{left:0, right:0, top:0, bottom:0},
              xAxis: {
                show:false,
                type: 'category',
                boundaryGap: false,
              },
              yAxis: {
                show:false,
                type: 'value'
              },
              series: [{
                data: [820, 932, 901, 934, 1290, 1330, 1320, 1330, 1290, 934, 901, 932,820,820, 932, 901, 934, 1290, 1330,1320, 1330, 1290, 934, 901, 932,820],
                type: 'line',
                symbolSize:0,   //拐点圆的大小
                areaStyle: {}
              }]
            },
            footTit:'-12.12%'
          },
          {
            title:'近七天降噪比',
            tooltipCont:'降噪比：聚类量/事件量',
            titCont:'65%',
            chart:[

            ],
            footTit:'+15.13%'
          }
        ]
      }
    },
    mounted() {
      this.drawBarEvent();
      this.drawBarAlarm();
      this.drawBarJutype();
      this.drawLineRes();
      this.drawLineHandleTime();
    },
    methods: {
      forId:function(index){
        return "myChart" +index
      },
      drawBarEvent(){
        let myChart = echarts.init(document.getElementById('myChart0'));
        myChart.setOption(this.chartsTemp[0].option);
      },
      drawBarAlarm(){
        let myChart = echarts.init(document.getElementById('myChart1'));
        myChart.setOption(this.chartsTemp[1].option);
      },
      drawLineRes(){
        let myChart = echarts.init(document.getElementById('myChart2'));
        myChart.setOption(this.chartsTemp[2].option);
      },
      drawBarJutype(){
        let myChart = echarts.init(document.getElementById('myChart3'));
        myChart.setOption(this.chartsTemp[3].option);
      },
      drawLineHandleTime(){
        let myChart = echarts.init(document.getElementById('myChart4'));
        myChart.setOption(this.chartsTemp[4].option);
      }
    }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .panel{
    background: #fff;
    border: 0;
    -webkit-border-radius: 5px;
    -moz-border-radius: 5px;
    border-radius: 5px;
    box-shadow: none !important;
    margin-bottom: 20px;
  }
  .panel-heading{
    position: relative;
    height: 57px;
    /*color: #4d627b;*/
    border-bottom: 1px solid transparent;
    border-top: 0;
    background: #fff;
    padding: 15px 15px 0;
  }
  .panel-control {
    height: 100%;
    position: relative;
    float: right;
    top: -5px;
  }
  .head-title {
    font-weight: normal;
    font-size: 14px;
    white-space: nowrap;
    overflow: hidden;
    text-overflow: ellipsis;
    margin: 0;
    margin-bottom: 5px;
  }
  .head-cont{
    font-size: 24px;
  }
  .panel-body{
    padding: 15px;
  }
  .chartsbox{
    height: 30px;
    /*border: 1px solid #f8f8f8;*/
  }
  .panel-footer{
    position: relative;
    height: 42px;
    border-bottom: 1px solid transparent;
    border-top: 0;
    background: #fff;
    padding: 0 15px;
  }
  .panel-footer .footer-title{
    border-top: 1px solid #f8f8f8;
    line-height: 42px;
  }
  .bg-success {
    background-color: #89d69b!important;
  }
</style>
