<template>
    <div v-bind:class="{'is-solved':bug.fixed}">
        <p class="bug-item">
            <input type="checkbox" v-on:change="markFixed">    
            {{bug.title}}<br>{{bug.description}}<br>{{bug.category}}<br>{{bug.severity}}
            <button @click="$emit('del-bug', bug.id)" class="del">x</button>
        </p>
    </div>
</template>

<script>
    export default {
        name:"BugItem",
        props:["bug"],
        methods:{
            markFixed(){
                this.bug.fixed = !this.bug.fixed;
            }
        }
    }
</script>

<style scoped>
    .bug-item{
        background-color:aqua;
        padding: 10px;
        border-bottom: 2px red dotted;
    }

    .is-solved{
        text-decoration: line-through;
    }

    .del{
        background: red;
        color: white;
        border: none;
        padding: 5px 5px;
        border-radius: 50%;
        cursor: pointer;
        float: right;
    }

</style>