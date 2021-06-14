<template>

  <section class="src-components-color-options">
    <div class="jumbotron">
      <div class="container">
        <div v-for="(color, index) in colorOptions" :key="index">
          <div class="square" v-bind:style="{ 'background-color': color }" @click="colorClick(color, index)"></div>
        </div>
      </div>
    </div>
  </section>

</template>

<script lang="js">

  export default  {
    name: 'src-components-color-options',
    props: {
      isHard : Boolean,
      colorOptions : Array,
      colorPicked: String
    },
    mounted () {

    },
    data () {
      return {

      }
    },
    methods: {
      colorClick(color, index){
        if(color == this.colorPicked){
          
          for (let index = 0; index < this.colorOptions.length; index++) {
            this.$set(this.colorOptions, index, this.colorPicked)           
          }

          this.$emit('win', "You Picked Right!")
        }
        else{
          let val = "rgb(" + 35 + ", " + 35 + ", " + 35 + ")";
          this.$set(this.colorOptions, index, val)
          this.$emit('tryAgain', "Try Again!")
        }
      }
    },
    computed: {

    }
}


</script>

<style scoped lang="css">
  .src-components-color-options {

  }

  .jumbotron{
    
  }

  .container {
    margin: 20px auto;
    max-width: 600px;
  }
  .square{
    width: 30%;
    background: blue;
    padding-bottom: 30%;
    float: left;
    margin: 1.66%;
    border-radius: 10%;
    transition: background 0.8s;
    -webkit-transition: background 0.8s;
    -moz-transition: background 0.8s;
  }
</style>
