<template>
  <div id="app">
    <div class="long" v-on:scroll="scrollHandler">
      <div class="long-container">
        <div class="segment">
          <div class="text" v-bind:style="style">
            Text
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>

  const longHeight = 500;
  const containerHeight = 5000;
  const segmentHeight = 200;

  export default {
    name: 'App',
    data(){
      return {
        scrollTop: 0,
        scrolled: null,
        style: {}
      };
    },
    methods: {
      scrollHandler(event){
        console.log(event.target.scrollTop);
        this.scrolled = event.target;

        const segmentStart = 0;
        const segmentEnd = segmentStart + segmentHeight;

        const scrollTop = event.target.scrollTop;

        if (scrollTop < 1500){
        } else if (scrollTop < 1700){
          this.style = {
            transform: `translateY(${(scrollTop - 1500) / 2}px)translateY(-50%)`
          }
        } else if (scrollTop < 2000){
          this.style = {
            transform: 'translateY(100px)translateY(-50%)'
          }
        } else if (scrollTop < 2200){
          this.style = {
            transform: `translateY(${(scrollTop - 2000 + 200) / 2}px)translateY(-50%)`
          }
        } else{
          this.style = {
          }
        }
      }
    }
  };
</script>

<style>

  * {
    box-sizing: border-box;
  }

  #app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
  }

  .long {
    height: 500px;
    border: 1px solid black;
    overflow: auto;
  }

  .long-container {
    height: 5000px;
    border: 1px solid black;
    position: relative;
  }

  .segment {
    top: 2000px;
    width: 100%;
    height: 200px;
    border: 1px solid black;
    position: absolute;
  }

  .text {
    pointer-events: none;
    /*top: 50%;*/
    will-change: transform;
    width: 100%;
    /*transform: translateY(-50%);*/
    /*position: absolute;*/
  }
</style>
