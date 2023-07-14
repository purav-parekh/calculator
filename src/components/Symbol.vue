<template>
    <button class="symbol" :style="{backgroundColor:bgColor}">
       {{ sign }}
    </button>    
</template>
  


<script>

  export default {
    name: 'Symbol',
    components: {
    },
    props: {
      sign: String,
      'bgColor': String
    },
  }
</script>
    
<style scoped>
  .symbol {
      height: 5em;
      width: 5em;
      text-align: center;
      border: 1px solid #eee;
      border-radius: 5px;
      color: #eee;
  }
</style>