<template>
    <div>
        <form @submit="addBug">
            <div class="outer">
                <div class="inner">
                    <label for="title">BUG TITLE:</label>
                    <input type="text" name="title" v-model="title" placeholder="add title..." required>
                    <br><br>
                </div>
                <div class="inner">
                    <label for="category">CATEGORY:</label>
                    <select name="category" required v-model="category">
                        <option value="0">Select Category</option>
                        <option value="1">Crash</option>
                        <option value="2">Softlock/Infinite Prosessing Turn</option>
                        <option value="3">Gameplay/Mechanics/Rules</option>
                        <option value="4">Balance</option>
                        <option value="5">Performance</option>
                        <option value="6">User Interface</option>
                        <option value="7">Graphical Glitch</option>
                        <option value="8">Typos</option>                                                              
                    </select>
                    <br><br>
                </div>
                <div class="inner">
                    <label for="severity">SEVERITY:</label>
                    <select name="severity" required v-model="severity">
                        <option value="0">Select Severity</option>
                        <option value="1">BLOCKER - Can't continue playing</option>
                        <option value="2">CRITICAL - Breaks game experience</option>
                        <option value="3">MAJOR - Diminish game experience</option>
                        <option value="4">MINOR - Minor problem</option>
                        <option value="5">TRIVIAL - Trivial problem</option>                                                            
                    </select>
                    <br><br>
                </div>            
                <div class="inner">
                    <label for="description">DESCRIPTION:</label>
                    <textarea rows="20" cols="50" name="description" placeholder="add description..." required v-model="description"></textarea>
                </div>
                <div class="inner">
                    <br><br>
                    <input type="submit" value="SEND" class="btn">
                    <br><br>
                </div>
            </div>
        </form>
    </div>
</template>

<script>

   // import {v4} from 'uuid';

    export default {
        name:"AddBug",
        data(){
            return {
                title: '', category: '', severity: '', description:''
            }
        },
        methods:{
            addBug(e){
                e.preventDefault();

                const newBug = {
                    //id: v4(),
                    title: this.title,
                    category: this.category,
                    severity: this.severity,
                    description: this.description,
                    filed: false
                } 

                // send up yo parent
                this.$emit('addBug', newBug);

                this.title = '';
                this.category = 0;
                this.severity = 0;
                this.description = '';
            }
        }
    }
</script>

<style scoped>
    form{
        width: 100%;
        min-width: 800px;
        margin: 0 auto;
    }

    input[type="text"]{
        flex: 10;
        padding: 5 px;
    }

    input[type="submit"]{
        flex: 2;
    }

    .outer{
        background: #999;padding:10px;
    }

    .inner{
        background:#ccc;
    }
</style>