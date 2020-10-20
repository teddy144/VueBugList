<template>
    <div>
        <header class="header">
            <h1>{{name}}</h1>
        </header>
    </div>
</template>

<script>
    export default {
        name:"Header",
        props: ["name"]
    }
</script>

<style scoped>
    .header{
        background: #333;
        color:white;
        text-align: center;
        padding: 10px;
    }

    .header a{
        color: white;
        padding-right: 5px;
    }
</style>