<template>
    <button @click="displayNum" class="num-btn">
       {{ num }}
    </button>    
</template>
    
    
    <script>
    
    export default {
      name: 'Number',
      props: {
        num: String
      },
      methods: {
        displayNum() {
            console.log('clicked',this.num)
        }
      }
    }
    </script>
    
    <style scoped>
    .num-btn {
        /* margin: auto; */
        border: 1px solid black;
        height: 5em;
        width: 5em;
        /* text-align: center */
    }
    </style>