<template>
  <div id='major'>
    1 = <sup v-if="true">#</sup> F
  </div>
</template>

<script>
  export default {
    name: 'major'

  }
</script>

<style scoped>
  #major {
    font-family: serif;
    font-style: italic;
    padding-bottom: 20px;
    height: 50px;
    font-size: 32px;
    color: #9c9c9c;
  }
</style>