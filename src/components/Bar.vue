<template>

  <section class="src-components-bar">
    <div class="jumbotron">
      <button id="reset" @click="resetGame()"> New colors</button>
      <span class="message" v-bind:style="{ color: message != '' ? '#000000' : '#ffffff' }"> {{message}} </span>

      <button id="easy" v-bind:style="{ color: !isHard ? 'white' : 'steelblue', 'background-color': !this.isHard ? 'steelblue' : 'white' }" @click="activeEasy()">easy</button>
      <button id="hard" v-bind:style="{ color: isHard ? 'white' : 'steelblue', 'background-color': this.isHard ? 'steelblue' : 'white' }" @click="activeHard()">hard</button>
    </div>
  </section>

</template>

<script lang="js">

  export default  {
    name: 'src-components-bar',
    props: {
      message: String
    },
    mounted () {
      let param = this.initParams()
      this.$emit('initGame', param)
    },
    data () {
      return {
        isHard: true,
      }
    },
    methods: {
      initParams(){
        let colors = this.createNewColors();
        let picked = this.pickedColor(colors);
        let param = {
          isHard: this.isHard, 
          colors: colors,
          colorPicked: picked
        };
        return param;
      },
      activeEasy(){
        if(this.isHard){
          this.isHard = false;
          let param = this.initParams()
          this.$emit('initGame', param)
        }
      },
      activeHard(){
        if(!this.isHard){
          this.isHard = true;
          let param = this.initParams()
          this.$emit('initGame', param)
        }
      },
      createNewColors(){
        var colors = [];
        let cant = this.isHard ? 6 : 3;
        for (var i = 0; i < cant; i++) {
          colors.push(this.createRandomStringColor());
        }
        return colors;
      },
      createRandomStringColor(){
        let newColor = "rgb(" + this.randomInt() + ", " + this.randomInt() + ", " + this.randomInt() + ")" ;
        return newColor;
      },
      randomInt(){
        return Math.floor(Math.random() * 256);
      },
      pickedColor(color){
        return color[Math.floor(Math.random()*color.length)]
      },
      resetGame(){
        let param = this.initParams()
        this.$emit('initGame', param)
      }
    },
    computed: {

    }
}


</script>

<style scoped lang="css">
  .src-components-bar {

  }

  .jumbotron {
    background: #ffffff;
    height: 30px;
    text-align: center;
    margin: 0;
    margin-top: -30px;
  }
  
  button {
    border: none;
    background-color: white;
    font-family: "Montserrat", "Avenir";
    text-transform: uppercase;
    height: 100%;
    font-weight: 700;
    letter-spacing: 1px;
    color: steelblue;
    transition: all 0.3s;
    outline: none;
  }
  
  .message {
    
    display: inline-block;
    width: 20%;
  }
  .selected {
    background-color: steelblue;
    color: white;
  }
</style>
