<template>
  <div id='baseNote'>
    1 = <sup v-if="false">#</sup> {{bNote}}
  </div>
</template>

<script>
  export default {
    name: 'major',
    props:['bNote'],


  }
</script>

<style scoped>
  #baseNote {
    font-family: serif;
    font-style: italic;
    padding-bottom: 20px;
    height: 50px;
    font-size: 32px;
    color: #9c9c9c;
  }
</style>