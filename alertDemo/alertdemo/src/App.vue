<template>
  <div id="app">
    <div id="page-content">
      <smallPanel></smallPanel>
      <largePanel></largePanel>
      <router-view/>
    </div>

  </div>
</template>

<script>
import './assets/iconfont/iconfont.css'

import smallPanel from '@/components/index/smallPanel'
import largePanel from '@/components/index/largePanel'

$(function () {
  $('[data-toggle="tooltip"]').tooltip();
});


export default {
  name: 'App',
  components: {
    smallPanel,
    largePanel
  }
}
</script>

<style>
  body{
    background:#ecf0f5;
    color: #555;
  }
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
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

</style>
