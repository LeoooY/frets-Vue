<template>
  <div id='string'>
    <span class="string-note">{{stringNote}}</span>
    <div class="string-segment" v-for="(el,idx) in 16" :key="idx">
      <div></div>
    </div>
  </div>
</template>

<script>
  export default {
    name: 'string',
    props: ['stringNote']
  }
</script>

<style scoped>
  #string {
    display: flex;
  }
  
  .string-note {
    width: 20px;
    color: #cacaca;
    line-height: 40px;
    margin-right: 10px;
  }
  

  .string-segment {
    display: inline-block;
    flex: 1;
    height: 40px;
    background: linear-gradient(transparent 18px, #ddd 18px, #ddd 22px, transparent 22px);
  }

  .string-segment::after {
    content: "";
    display: block;
    height: 40px;
    width: 1px;
    background-color: #ddd;
    float: right;
    margin-top: 20px;
  }
  
  
  
</style>