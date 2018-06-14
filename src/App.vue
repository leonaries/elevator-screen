<template>
  <div id="app">
      <header id="header" style="text-align: center">
          梯外屏展示Demo
      </header>
       <section>
         <ViewBox></ViewBox>
         <ViewList></ViewList>
       </section>
  </div>
</template>

<script>
  import ViewBox from '@/components/ViewBox' //广告泳道图展示区域
  import ViewList from '@/components/ViewList' //广告选择列表区域
  export default {
    name: 'App',
    components:{
      ViewBox,
      ViewList
    }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}
  #header{
    color: red;
    font-size: 50px;
  }
</style>
