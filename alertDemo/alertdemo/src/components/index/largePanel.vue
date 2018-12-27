<template>
  <div class="row">
    <div :class="node.class" v-for="(node,index) in charts_template">
      <div class="panel">
        <div class="panel-header">
          <div class="panel-control">
            <i class="iconfont icon-shezhi" data-toggle="dropdown"></i>
            <div class="dropdown-menu dropdown-menu-right">
              <a class="dropdown-item" href="#">最近7天告警</a>
              <a class="dropdown-item" href="#">最近15天告警</a>
              <a class="dropdown-item" href="#">最近30天告警</a>
              <div v-show="node.chartType !='diffAlarm'" class="dropdown-divider"></div>
              <a v-show="node.chartType !='diffAlarm'" class="dropdown-item" data-toggle="modal" data-target="#exampleModal" href="#">重新选择报表</a>
              <a v-show="node.chartType !='diffAlarm'" class="dropdown-item" href="#">删除</a>
            </div>
          </div>
          <h3 class="panel-title">{{node.title}}</h3>
        </div>
        <div class="panel-body">
          <div v-if="node.chartType != 'recentlyAlarm'" class="bigchartsbox" :id="panelforId(index)"></div>
          <div v-if="node.chartType == 'recentlyAlarm'" class="bigchartsbox">
            <div class="recentAlarm">
              <div class="state fr">
                <span><i class="icon-circle success"></i>全部（99+）</span>
                <span><i class="icon-circle danger"></i>严重（99+）</span>
                <span><i class="icon-circle warning"></i>警告（99+）</span>
                <span><i class="icon-circle remind"></i>提醒（99+）</span>
              </div>
              <div class="">近5条</div>
            </div>
            <div class="alarmtable">
              <table class="table table-bordered">
                <thead>
                <tr>
                  <th scope="col">发生时间</th>
                  <th scope="col">级别</th>
                  <th scope="col">告警内容</th>
                </tr>
                </thead>
                <tbody>
                <tr>
                  <td>2018-12-25 14:46:25</td>
                  <td><i class="icon-circle warning"></i></td>
                  <td>主机ping不通</td>
                </tr>
                <tr>
                  <td>2018-12-25 14:46:25</td>
                  <td><i class="icon-circle warning"></i></td>
                  <td>主机ping不通</td>
                </tr>
                <tr>
                  <td>2018-12-25 14:46:25</td>
                  <td><i class="icon-circle warning"></i></td>
                  <td>主机ping不通</td>
                </tr>
                <tr>
                  <td>2018-12-25 14:46:25</td>
                  <td><i class="icon-circle warning"></i></td>
                  <td>主机ping不通</td>
                </tr>
                <tr>
                  <td>2018-12-25 14:46:25</td>
                  <td><i class="icon-circle warning"></i></td>
                  <td>主机ping不通</td>
                </tr>
                </tbody>
              </table>
            </div>
          </div>
        </div>
      </div>
    </div>

    <div class="col-md-4">
      <div class="panel">
        <div class="panel-header">
        </div>
        <div class="panel-body">
          <div class="bigchartsbox addBox"><i class="iconfont icon-tianjia"></i></div>
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
  require('echarts/lib/chart/pie');
  // 引入提示框和title组件
  require('echarts/lib/component/tooltip');
  require("echarts/lib/component/markPoint");
  require("echarts/lib/component/title");
  require("echarts/lib/component/legendScroll");
  //引入主题
  require("echarts/theme/macarons");

  export default {
    name: 'Index',
    data () {
      return {
        charts_template:[
          {
            title:'不同分类告警趋势分析',
            class:'col-md-8',
            chartType:'diffAlarm',
            option : {
              grid:{left:40, right:20, bottom:20},
              title : {
                text: '某地区蒸发量和降水量',
                subtext: '纯属虚构'
              },
              tooltip : {
                trigger: 'axis'
              },
              legend: {
                icon: "circle",
                right:'0',
                data:['蒸发量','降水量']
              },
              calculable : true,
              xAxis : [
                {
                  type : 'category',
                  data : ['1月','2月','3月','4月','5月','6月','7月','8月','9月','10月','11月','12月']
                }
              ],
              yAxis : [
                {
                  type : 'value'
                }
              ],
              series : [
                {
                  name:'蒸发量',
                  type:'bar',
                  data:[2.0, 4.9, 7.0, 23.2, 25.6, 76.7, 135.6, 162.2, 32.6, 20.0, 6.4, 3.3],
                  markPoint : {
                    data : [
                      {name : '访问量', value : 2.0, xAxis: 0, yAxis: 2.0},
                      {name : '访问量', value : 4.9, xAxis: 1, yAxis: 4.9},
                      {name : '访问量', value : 7.0, xAxis: 2, yAxis: 7.0},
                      {name : '访问量', value : 23.2, xAxis: 3, yAxis: 23.2},
                      {name : '访问量', value : 25.6, xAxis: 4, yAxis: 25.6},
                      {name : '访问量', value : 76.7, xAxis: 5, yAxis: 76.7},
                      {name : '访问量', value : 135.6, xAxis: 6, yAxis: 135.6},
                      {name : '访问量', value : 162.2, xAxis: 7, yAxis: 162.2},
                      {name : '访问量', value : 32.6, xAxis: 8, yAxis: 32.6},
                      {name : '访问量', value : 20.0, xAxis: 9, yAxis: 20.0},
                      {name : '访问量', value : 6.4, xAxis: 10, yAxis: 6.4},
                      {name : '访问量', value : 3.3, xAxis: 11, yAxis: 3.3}
                    ]
                  },
                  markLine : {
                    data : [
                      {type : 'average', name: '平均值'}
                    ]
                  }
                },
                {
                  name:'降水量',
                  type:'bar',
                  data:[2.6, 5.9, 9.0, 26.4, 28.7, 70.7, 175.6, 182.2, 48.7, 18.8, 6.0, 2.3],
                  markPoint : {
                    data : [
                      {name : '访问量', value : 2.6, xAxis: 0, yAxis: 2.6},
                      {name : '访问量', value : 5.9, xAxis: 1, yAxis: 5.9},
                      {name : '访问量', value : 9.0, xAxis: 2, yAxis: 9.0},
                      {name : '访问量', value : 26.4, xAxis: 3, yAxis: 26.4},
                      {name : '访问量', value : 28.7, xAxis: 4, yAxis: 28.7},
                      {name : '访问量', value : 70.7, xAxis: 5, yAxis: 70.7},
                      {name : '访问量', value : 175.6, xAxis: 6, yAxis: 175.6},
                      {name : '访问量', value : 182.2, xAxis: 7, yAxis: 182.2},
                      {name : '访问量', value : 48.7, xAxis: 8, yAxis: 48.7},
                      {name : '访问量', value : 18.8, xAxis: 9, yAxis: 18.8},
                      {name : '访问量', value : 6.0, xAxis: 10, yAxis: 6.0},
                      {name : '访问量', value : 2.3, xAxis: 11, yAxis: 2.3}
                    ]
                  },
                  markLine : {
                    data : [
                      {type : 'average', name : '平均值'}
                    ]
                  }
                }
              ]
            }
          },
          {
            title:'告警级别&状态分析',
            class:'col-md-4',
            chartType:'alarmLevel',
            option : {
              // grid:{left:40, right:20, bottom:20},
              tooltip: {
                trigger: 'item',
                formatter: "{a} <br/>{b}: {c} ({d}%)"
              },
              legend: {
                icon: "circle",
                orient: 'vertical',
                // x: 'right',
                right:0,
                data:['直达','营销广告','搜索引擎','邮件营销','联盟广告','视频广告','百度','谷歌','必应','其他']
              },
              series: [
                {
                  name:'访问来源',
                  type:'pie',
                  selectedMode: 'single',
                  radius: [0, '30%'],

                  label: {
                    normal: {
                      position: 'inner'
                    }
                  },
                  labelLine: {
                    normal: {
                      show: false
                    }
                  },
                  data:[
                    {value:335, name:'直达', selected:true},
                    {value:679, name:'营销广告'},
                    {value:1548, name:'搜索引擎'}
                  ]
                },
                {
                  name:'访问来源',
                  type:'pie',
                  radius: ['40%', '55%'],
                  data:[
                    {value:335, name:'直达'},
                    {value:310, name:'邮件营销'},
                    {value:234, name:'联盟广告'},
                    {value:135, name:'视频广告'},
                    {value:1048, name:'百度'},
                    {value:251, name:'谷歌'},
                    {value:147, name:'必应'},
                    {value:102, name:'其他'}
                  ]
                }
              ]
            }
          },
          {
            title:'成员效率分析',
            class:'col-md-4',
            chartType:'MemberAnaly',
            option : {
              tooltip : {
                trigger: 'axis',
                axisPointer : {            // 坐标轴指示器，坐标轴触发有效
                  type : 'shadow'        // 默认为直线，可选为：'line' | 'shadow'
                },
                formatter: function (params, ticket, callback) {
                  console.log(params)
                  var res = params[0].name ;
                  for (var i = 0, l = params.length; i < l; i++) {
                    res += '<br/>' + params[i].seriesName + ' : ' + Math.abs(params[i].value) ;
                  }
                  setTimeout(function () {
                    // 仅为了模拟异步回调
                    callback(ticket, res);
                  }, 500)
                  return 'loading...';
                }
              },
              legend: {
                icon:'circle',
                right:0,
                data:[ '男', '女']
              },
              grid: {
                left: '3%',
                right: '4%',
                bottom: '3%',
                containLabel: true
              },
              xAxis : [
                {
                  axisLabel : { formatter: function (value){return Math.abs(value);//显示的数值都取绝对值
                    }
                  },
                  type : 'value'
                }
              ],
              yAxis : [
                {
                  type : 'category',
                  axisTick : {show: false},
                  // data : ['0~5岁','5~10岁','10-30岁','30-50岁','50-70岁','70-100','100以上']
                  data : ['成员1','成员2','成员3','成员4','成员5','成员6','成员7']
                }
              ],
              series : [
                {
                  name:'男',
                  type:'bar',
                  stack: '总量',
                  label: {
                    normal: {
                      show: true,
                      // position: 'right',

                    }
                  },
                  // data:[320, 302, 341, 374, 390, 450, 420]
                  data:[1100, 542, 318, 881, 631, 450, 420]
                },
                {
                  name:'女',
                  type:'bar',
                  stack: '总量',
                  label: {
                    normal: {
                      show: true,
                      // position: 'left',
                      formatter:function(v){return Math.abs(v.data)}  //负数去掉- 显示为整数
                    }
                  },

                  // data:[-120, -132, -101, -134, -190, -230, -210]
                  data:[-350, -742, -218, -381, -521, -230, -210]
                }
              ]
            }
          },
          {
            title:'降噪分析',
            class:'col-md-4',
            chartType:'NoiseAnaly',
            option : {
              title: {
                text: '堆叠区域图'
              },
              tooltip : {
                trigger: 'axis',
                axisPointer: {
                  type: 'cross',
                  label: {
                    backgroundColor: '#6a7985'
                  }
                }
              },
              legend: {
                right:0,
                data:['邮件营销','联盟广告','视频广告','直接访问','搜索引擎']
              },
              grid: {
                left: '3%',
                right: '4%',
                bottom: '3%',
                containLabel: true
              },
              xAxis : [
                {
                  type : 'category',
                  boundaryGap : false,
                  data : ['周一','周二','周三','周四','周五','周六','周日']
                }
              ],
              yAxis : [
                {
                  type : 'value'
                }
              ],
              series : [
                {
                  name:'邮件营销',
                  type:'line',
                  stack: '总量',
                  areaStyle: {},
                  data:[120, 132, 101, 134, 90, 230, 210]
                },
                {
                  name:'联盟广告',
                  type:'line',
                  stack: '总量',
                  areaStyle: {},
                  data:[220, 182, 191, 234, 290, 330, 310]
                },
                {
                  name:'视频广告',
                  type:'line',
                  stack: '总量',
                  areaStyle: {},
                  data:[150, 232, 201, 154, 190, 330, 410]
                },
                {
                  name:'直接访问',
                  type:'line',
                  stack: '总量',
                  areaStyle: {normal: {}},
                  data:[320, 332, 301, 334, 390, 330, 320]
                },
                {
                  name:'搜索引擎',
                  type:'line',
                  stack: '总量',
                  label: {
                    normal: {
                      show: true,
                      position: 'top'
                    }
                  },
                  areaStyle: {normal: {}},
                  data:[820, 932, 901, 934, 1290, 1330, 1320]
                }
              ]
            }
          },
          {
            title:'最近告警',
            class:'col-md-4',
            chartType:'recentlyAlarm'
          },
        ]
      }
    },
    mounted() {
      this.drawBarDiffAlarm();
      this.drawBarAlarmlevel();
      this.drawBarMemberAnaly();
      this.drawBarNoiseAnaly();
    },
    methods: {
      panelforId:function(index){
        return "sysChart" +index
      },
      drawBarDiffAlarm(){
        let myChart = echarts.init(document.getElementById('sysChart0'),'macarons');
        myChart.setOption(this.charts_template[0].option);
      },
      drawBarAlarmlevel(){
        let myChart = echarts.init(document.getElementById('sysChart1'));
        myChart.setOption(this.charts_template[1].option);
      },
      drawBarMemberAnaly(){
        let myChart = echarts.init(document.getElementById('sysChart2'),'macarons');
        myChart.setOption(this.charts_template[2].option);
      },
      drawBarNoiseAnaly(){
        let myChart = echarts.init(document.getElementById('sysChart3'));
        myChart.setOption(this.charts_template[3].option);
      },
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
  .panel-header,.panel-footer{
    position: relative;
    height: 42px;
    border-bottom: 1px solid transparent;
    padding: 0 15px;
  }
  .panel-control {
    height: 100%;
    position: relative;
    float: right;
    padding: 8px 0 0 5px;
  }
  .panel-title {
    font-weight: bold;
    font-size: 14px;
    line-height: 42px;
    white-space: nowrap;
    overflow: hidden;
    text-overflow: ellipsis;
    margin: 0;
  }
  .panel-body{
    padding: 0 15px 15px;
  }

  .bigchartsbox{
    height: 330px;
  }
  .recentAlarm{
    position: relative;
    font-size: 14px;
    height: 36px;
  }

  .addBox {
    text-align: center;
  }
  .addBox i{
    font-size: 60px;
    color: #ddd;
    line-height: 318px;
  }
</style>
