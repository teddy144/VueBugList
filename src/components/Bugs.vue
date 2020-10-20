<template>
    <div>
        <div v-bind:key="bug.id" v-for ="bug in bugs" class="buglist">
            <BugItem v-bind:bug="bug" v-on:del-bug="$emit('del-bug', bug.id)"/>

        </div>
    </div>
</template>

<script>
    import BugItem from './BugItem.vue'

    export default {
        name: "Bugs",
        components:
        {
            BugItem
        },
        props:["bugs", name]
    }
</script>

<style scoped>
    .buglist{
        width: 100%;
        min-width: 800px;
        margin: 0 auto;
    }
</style>