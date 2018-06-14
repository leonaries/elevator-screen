<template>
<div id="all">
  <div class="dragbox">
      <div class="adLeft" @drop="drop"
           @dragover="allowDrop">
        <div class="draglist red" title="拖拽" draggable="true" id="welfare5s" @dragstart="drag">公益广告5S</div>
        <div class="draglist blue" title="拖拽" draggable="true" id="welfare10s"  @dragstart="drag">公益广告10S</div>
        <div class="draglist yellow" title="拖拽" draggable="true" id="welfare15s"  @dragstart="drag">公益广告15S</div>
      </div>
    <div class="adRight" @drop="drop"
         @dragover="allowDrop">
      <div class="draglist green" title="拖拽" draggable="true" id="ad5s"  @dragstart="drag">房地产广告5S</div>
      <div class="draglist green" title="拖拽" draggable="true" id="2ad5s"  @dragstart="drag">房地产2广告5S</div>
      <div class="draglist darkorange" title="拖拽" draggable="true" id="ad7.5s"  @dragstart="drag">食品广告7.5S</div>
      <div class="draglist darkorange" title="拖拽" draggable="true" id="2ad7.5s"  @dragstart="drag">食品2广告7.5S</div>
      <div class="draglist gray" title="拖拽" draggable="true" id="ad10s"  @dragstart="drag">医院广告10S</div>
      <div class="draglist gray" title="拖拽" draggable="true" id="2ad10s"  @dragstart="drag">医院2广告10S</div>
      <div class="draglist pink" title="拖拽" draggable="true" id="ad15s"  @dragstart="drag">汽车广告15S</div>
      <div class="draglist pink" title="拖拽" draggable="true" id="2ad15s"  @dragstart="drag">汽车2广告15S</div>
      <div class="draglist chocolate" title="拖拽" draggable="true" id="ad30s"  @dragstart="drag">美容广告30S</div>
    </div>
  </div>
</div>
</template>

<script>
    export default {
        name: "view-list",
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
            console.log("123")
            if(ev.target.className =='upScreen' ||ev.target.className == 'downScreen' ||ev.target.className == 'adRight' ||ev.target.className == 'adLeft' ){
              if(data.indexOf('welfare') != '-1'){
                document.getElementById(data).parentNode.removeChild(document.getElementById(data))
              }else {
                ev.target.appendChild(document.getElementById(data));
              }
            }
          }
    }
    }
</script>

<style lang="less">
  #all{
    width: 100%;
    margin: 0 auto;
    .dragbox{
      display: flex;
      justify-content: space-around;
      .adLeft,.adRight{
        width: 100%;
        min-height: 200px;
        border: 1px solid black;
        margin-top: 70px;
        position: relative;
      }
      .adLeft{
        width: 60%;
      }
    }
  }
  .adLeft:before{
    content: "上下屏广告区域的公益广告移入此处可清除掉(注意 未排版的公益广告不要移入此处）";
    position: absolute;
    max-width: 300px;
    left: 70%;
    top: 50%;
    transform: translate(-50%);
    font-size: 16px;
  }
  .draglist{
    text-align: center;
    line-height: 100%;
    height: 100%;
    display: inline-block;
    vertical-align: middle;
    outline: 1px solid black;
    font-size: 30px;
  }
  .red{
    width: 50px;
    background-color: red;
    color: black;
  }
  .blue{
    width: 100px;
    background-color: blue;
    color: white;
  }
  .yellow{
    width: 150px;
    background-color: yellow;
    color: black;
  }
  .green{
    width: 50px;
    background-color: green;
    color: white;
  }
  .pink{
    width: 150px;
    background-color: pink;
    color: black;
  }
  .gray{
    width: 100px;
    background-color: gray;
    color: white;
  }
  .chocolate{
    width: 300px;
    background-color: chocolate;
    color: white;
  }
  .darkorange{
    width: 75px;
    background-color: darkorange;
    color: black;
  }



</style>
