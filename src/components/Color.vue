<template>

  <section class="src-components-color">
    <div class="jumbotron" v-bind:style="{ 'background-color': activeBGC ? colorPicked : 'steelblue' }">
      <h1>The Great <br>
        <span class="colorDisplay"> {{colorPicked}} </span><br>
        Guessing Game
      </h1>
    </div>
  </section>

</template>

<script lang="js">

  export default  {
    name: 'src-components-color',
    props: {
      colorPicked: String,
      activeBGC: Boolean
    },
    mounted () {

    },
    data () {
      return {

      }
    },
    methods: {

    },
    computed: {

    }
}


</script>

<style scoped lang="css">
  .src-components-color {

  }
  .jumbotron {
    transition: all 0.3s;
    background: steelblue;
    text-transform: uppercase;
    text-align: center;
    margin: 0;
    color: white;
  }
  
  h1 {
    font-weight: normal;
    line-height: 1.1;
    padding: 20px 0;
  }

  .colorDisplay {
    font-size: 200%;
  }
</style>
