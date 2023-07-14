<template>
    <button class="btn" >
        {{ value }}
    </button>
</template>

<script>
    export default {
        name: 'btn',
        props: {
            value: Number,
        },
    }
</script>


<style scoped>
    .btn {
        height: 5em;
        width: 5em;
        background-color: #232323;
        color: #eee;
        border: 1px solid #eee;
        border-radius: 5px;
    }


</style>