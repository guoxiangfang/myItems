<template>
  <div class="row">
    <div class="col-md-2">
      <div class="panel">
        <div class="panel-heading">
          <div class="panel-control"><i class="iconfont icon-bangzhu"></i></div>
          <h3 class="panel-title">近7天所有事件</h3>
        </div>
        <h1 class="panel-cont">100</h1>
        <div class="panel-body">
          <div class="chartsbox" id="eventBarChart"></div>
        </div>
        <div class="panel-footer">
          <p class="panel-title">周环比 +12.12</p>
        </div>
      </div>
    </div>
    <div class="col-md-2">
      <div class="panel">
        <div class="panel-heading">
          <div class="panel-control"><i class="iconfont icon-bangzhu"></i></div>
          <h3 class="panel-title">近7天所有事件</h3>
        </div>
        <h1 class="panel-cont">100</h1>
        <div class="panel-body">
          <div class="chartsbox" id="eventBarChart"></div>
        </div>
        <div class="panel-footer">
          <p class="panel-title">周环比 +12.12</p>
        </div>
      </div>
    </div>
    <div class="col-md-2">
      <div class="panel">
        <div class="panel-heading">
          <div class="panel-control"><i class="iconfont icon-bangzhu"></i></div>
          <h3 class="panel-title">近7天所有事件</h3>
        </div>
        <h1 class="panel-cont">100</h1>
        <div class="panel-body">
          <div class="chartsbox" id="eventBarChart"></div>
        </div>
        <div class="panel-footer">
          <p class="panel-title">周环比 +12.12</p>
        </div>
      </div>
    </div>
    <div class="col-md-2">
      <div class="panel">
        <div class="panel-heading">
          <div class="panel-control"><i class="iconfont icon-bangzhu"></i></div>
          <h3 class="panel-title">近7天所有事件</h3>
        </div>
        <h1 class="panel-cont">100</h1>
        <div class="panel-body">
          <div class="chartsbox" id="eventBarChart"></div>
        </div>
        <div class="panel-footer">
          <p class="panel-title">周环比 +12.12</p>
        </div>
      </div>
    </div>
    <div class="col-md-2">
      <div class="panel">
        <div class="panel-heading">
          <div class="panel-control"><i class="iconfont icon-bangzhu"></i></div>
          <h3 class="panel-title">近7天所有事件</h3>
        </div>
        <h1 class="panel-cont">100</h1>
        <div class="panel-body">
          <div class="chartsbox" id="eventBarChart"></div>
        </div>
        <div class="panel-footer">
          <p class="panel-title">周环比 +12.12</p>
        </div>
      </div>
    </div>
    <div class="col-md-2">
      <div class="panel">
        <div class="panel-heading">
          <div class="panel-control"><i class="iconfont icon-bangzhu"></i></div>
          <h3 class="panel-title">近7天所有事件</h3>
        </div>
        <h1 class="panel-cont">100</h1>
        <div class="panel-body">
          <div class="chartsbox" id="eventBarChart"></div>
        </div>
        <div class="panel-footer">
          <p class="panel-title">周环比 +12.12</p>
        </div>
      </div>
    </div>
  </div>

</template>

<script>

// import smallPanel from 'components/index/smallPanel'
// import largePanel from 'components/index/largePanel'
export default {
  name: 'idnex',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App'
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  h1, h2,h3,h4,h5,h6 {
    margin: 0;
    font-weight: normal;
  }
  ul {
    list-style-type: none;
    padding: 0;
  }
  li {
    display: inline-block;
    margin: 0 10px;
  }
  a {
    color: #42b983;
  }
  .panel{
    background: #fff;
    border: 0;
    -webkit-border-radius: 5px;
    -moz-border-radius: 5px;
    border-radius: 5px;
    box-shadow: none !important;
    margin-bottom: 20px;
  }
  .panel-heading,.panel-footer{
    /*border-top-left-radius: 2px;*/
    /*border-top-right-radius: 2px;*/
    position: relative;
    height: 42px;
    color: #4d627b;
    border-bottom: 1px solid transparent;
    padding: 0 20px 0 20px;
  }
  .panel-control {
    height: 100%;
    position: relative;
    float: right;
    padding: 8px 15px 0 5px;
  }
  .panel-title {
    font-weight: normal;
    /*padding: 0 20px 0 20px;*/
    font-size: 14px;
    line-height: 42px;
    white-space: nowrap;
    overflow: hidden;
    text-overflow: ellipsis;
    margin: 0;
  }
  .panel-cont{
    padding: 0 20px 0 20px;
    font-size: 24px;
  }
  .panel-body{
    padding: 15px 20px;
  }
  .chartsbox{
    height: 30px;
    border: 1px solid #f8f8f8;
  }

  .panel-footer .panel-title{
    border-top: 1px solid #f8f8f8;
  }

</style>
