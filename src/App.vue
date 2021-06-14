<template>
  <div id="app">
    <div class="jumbotron">
      <br>
      <Color :colorPicked="picked" :activeBGC="activeBackgroundColor" />
      <Bar @initGame="generateNewGame($event)" :message="messageInfo"/>
      <ColorOption :isHard="isHardSelected" :colorOptions="colors" :colorPicked="picked"  @win="winGame($event)" @tryAgain="continueGame($event)"/>
    </div>
  </div>
</template>

<script>
import Color from './components/Color.vue'
import Bar from './components/Bar.vue'
import ColorOption from './components/ColorOptions.vue'

export default {
  name: 'App',
  components: {
    Color,
    Bar,
    ColorOption
  },
  data() {
    return {
      isHardSelected: true,
      colors: [],
      picked: "",
      activeBackgroundColor: false,
      messageInfo: ""
    }
  },
  methods:{
    generateNewGame($event){
      this.isHardSelected = $event.isHard;
      this.colors = $event.colors;
      this.picked = $event.colorPicked;
      this.activeBackgroundColor = false;
      this.messageInfo = "";
    },
    winGame($event){
      this.activeBackgroundColor = true;
      this.messageInfo = $event;
    },
    continueGame($event){
      this.messageInfo = $event;
    }
  }
}
</script>

<style scoped lang="css">
  #app {

  }

  h1 {
    color: rgb(5 36 68);
  }
  .jumbotron {
    background: #232323;
  }
</style>
