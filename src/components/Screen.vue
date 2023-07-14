<template>
    <div class="screen">
        {{ val }}
    </div>
</template>
    
    
<script>
    export default {
    name: 'Screen',
    props: {
        val:String,
    },
    methods: {
    },
}
</script>
    
<style scoped>
    .screen {
        text-align: center;
        border: 1px solid black;
        height: 12.5em;
        width: 17em;
        background-color: rgb(238, 238, 238);
        border: 1px solid white;
        border-radius: 5px;
    }
</style>