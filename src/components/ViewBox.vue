<template>
<div id="all">
  <div class="title">梯外屏广告泳道图</div>
  <div class="view">
    <div class="upScreen" id="div1" @ondrop="drop(event)"
         @ondragover="allowDrop(event)"></div>
    <div class="downScreen"></div>
  </div>
  <div class="dragremind"></div>
</div>
</template>

<script>
    export default {
        name: "view-box",
      methods:{
        allowDrop(ev) {
          ev.preventDefault();
        },
        drag(ev) {
          ev.dataTransfer.setData("Text",ev.target.id);
        },
        drop(ev) {
          ev.preventDefault();
          let data=ev.dataTransfer.getData("Text");
          ev.target.appendChild(document.getElementById(data));
        }

      }
    }
</script>

<style lang="less" scoped>
    .view{
      border: 1px solid black;
      height: 50vh;
      width: 100%;
      margin: 30px auto;
      .upScreen,.downScreen{
        border: 1px solid red;
        height: 25vh;
      }
    }
</style>
