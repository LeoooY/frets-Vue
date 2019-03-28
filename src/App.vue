<template>
  <div id="app">
    <!-- <div id="nav">
      <router-link to="/">Home</router-link> |
      <router-link to="/about">About</router-link>
    </div>
    <router-view/> -->
    <string class="" :stringNote="el" :key="idx" v-for="(el,idx) in EMPTY_SCALES"></string>
    <div class="fret-index">
      <span  :key="idx" v-for="(el,idx) in 16">{{idx}}</span>
    </div>
    <major></major>
  </div>
</template>
<script>
  import string from './components/string.vue'
  import major from './components/major.vue'

  export default {
    name: 'app',
    components: {
      string,
      major
    },
    data() {
      return {
        EMPTY_SCALES: ['E', 'B', 'G', 'D', 'A', 'E'],
        STRING_DIFFS: [5, 4, 5, 5, 5],
        NOTE_DIFFS: [2, 2, 1, 2, 2, 2, 1]
      }
    }
  }
</script>


<style>
  #app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin:10%;
    
  }

  #nav {
    padding: 30px;
  }

  #nav a {
    font-weight: bold;
    color: #2c3e50;
  }

  #nav a.router-link-exact-active {
    color: #42b983;
  }

  
  .fret-index{
    width: 100%;
    color: #cacaca;
    /* max-width: 1300px; */
    min-width: 750px;
    margin: 0 auto;
    display: flex;
  }
  .fret-index span{
    display: inline-block;
    flex: 1;
    height: 40px;
  }
  
  #string:nth-child(6) .string-segment::after{
    display: none;
  }
</style>