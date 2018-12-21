<template>
  <div id="app">
    <!--<img src="./assets/logo.png">-->
    <div id="page-content">
      <router-view/>
    </div>

  </div>
</template>

<script>
import './assets/iconfont/iconfont.css'
export default {
  name: 'App'
}
</script>

<style>
  body{
    background:#ecf0f5;
  }
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  /*text-align: center;*/
  color: #2c3e50;
  /*margin-top: 60px;*/
}
#page-content {
   padding: 20px 20px 0;
 }
  *{
    margin: 0;
    padding: 0;
  }
  .row {
    margin: 0 -10px;
  }
  [class^="col-"]:not(.pad-no) {
    padding-left: 10px;
    padding-right: 10px;
  }

</style>
