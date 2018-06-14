<template>
<div id="all">
  <div class="view">
    <div class="upScreen" id="div1" @drop="drop"
         @dragover="allowDrop">
    </div>
    <div class="downScreen" id="div2" @drop="drop"
         @dragover="allowDrop">
    </div>
  </div>
  <div class="dragremind"></div>
</div>
</template>

<script>
    export default {
      name: "view-box",
      data(){
        return {

        }
      },
      methods:{
        //拖拽广告DIV 开始时执行的函数
        drag(ev) {
          ev.dataTransfer.setData("Text",ev.target.id);
        },
        //拖拽元素 在目标元素内移动时执行的函数
        allowDrop(ev) {
          ev.preventDefault();
        },
        //拖拽元素进入目标元素，同时鼠标松开的时候
        drop(ev) {
          ev.preventDefault();
          let data=ev.dataTransfer.getData("Text");
          let item = document.getElementById(data).cloneNode(true);
          item.ondragstart = this.drag;
          //判断是否为拖入入广告位区域
          if(ev.target.className =='upScreen' ||ev.target.className == 'downScreen' ||ev.target.className == 'adRight' ||ev.target.className == 'adLeft' ){
            //判断拖动的是公益广告还是普通广告
            if(data.indexOf('ad') != '-1'){
              ev.target.appendChild(document.getElementById(data));
            }else {
              ev.target.appendChild(item);
            }
          }
        }
      }
    }
</script>

<style lang="less" scoped>
    .view{
      height: 50vh;
      width: 100%;
      margin: 30px auto;
      .upScreen,.downScreen{
        border: 1px solid red;
        height: 25vh;
        position: relative;
      }
      .upScreen:before{
        content: '上屏广告区域';
        position: absolute;
        left: 50%;
        top: -20%;
        transform: translateX(-50%);
        font-weight: bold;
        font-size: 30px;
      }
      .downScreen:before{
        content: '下屏广告区域';
        position: absolute;
        left: 50%;
        bottom: -20%;
        transform: translateX(-50%);
        font-weight: bold;
        font-size: 30px;
      }
    }
</style>
