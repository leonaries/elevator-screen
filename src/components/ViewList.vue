<template>
<div id="all">
  <div class="dragbox">
      <div class="adLeft">
        <div class="draglist red" title="拖拽" draggable="true" id="drag1"
             @ondragstart="drag(event)">公益广告5S</div>
        <div class="draglist blue" title="拖拽" draggable="true">公益广告10S</div>
        <div class="draglist yellow" title="拖拽" draggable="true">公益广告15S</div>
      </div>
    <div class="adRight">
      <div class="draglist green" title="拖拽" draggable="true">房地产广告10S</div>
      <div class="draglist gray" title="拖拽" draggable="true">医院广告20S</div>
      <div class="draglist pink" title="拖拽" draggable="true">骑车广告30S</div>
    </div>
  </div>
</div>
</template>

<script>
    export default {
        name: "view-list",
        methods:{
           allowDrop(ev) {
              ev.preventDefault();
            },

           drag(ev) {
              ev.dataTransfer.setData("Text",ev.target.id);
              console.log("123")
           },
          drop(ev) {
            ev.preventDefault();
            var data=ev.dataTransfer.getData("Text");
            ev.target.appendChild(document.getElementById(data));
          }

    }
    }
</script>

<style lang="less" scoped>
  #all{
    width: 100%;
    margin: 0 auto;
    .dragbox{
      display: flex;
      justify-content: space-around;
      .adLeft,.adRight{
        width: 100%;
        .draglist{
          height: 50px;
          border: 1px solid black;
          line-height: 50px;
        }
      }
    }
  }
  .red{
    background-color: red;
    color: black;
  }
  .blue{
    background-color: blue;
    color: white;
  }
  .yellow{
    background-color: yellow;
    color: black;
  }
  .green{
    background-color: green;
    color: white;
  }
  .pink{
    background-color: pink;
    color: black;
  }
  .gray{
    background-color: gray;
    color: black;
  }


</style>
