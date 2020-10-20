<template>
  <div id="app">
    
    <div class="container">
      <div class="left">
        <Header name="Bugs list"/>
        <Bugs v-bind:bugs="bugs" v-on:del-bug="deleteBug" />
      </div>
      <div class="right">
        <Header name="Bug form"/>
        <AddBug v-on:addBug="addBug"/>
      </div>
    </div>

  </div>
</template>

<script>
import Header from './components/Layout/Header';
import Bugs from './components/Bugs'
import AddBug from './components/AddBug'
import axios from 'axios';

export default {
  name: 'app',
  components: {
    Header,
    Bugs,
    AddBug
  },
  data(){
    return{bugs:[

    ]}

      /*
      {id:1,title:"title1", description: "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.", category:1, severity:2,fixed:false},
      {id:2,title:"title2", description: "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.", category:1, severity:2,fixed:true},
      {id:3,title:"title3", description: "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.", category:1, severity:2,fixed:false}      
    */

  },
  methods:{
    deleteBug(id){
      this.bugs = this.bugs.filter(bug => bug.id !== id)
    },
    addBug(newBug){

      const {title , category, severity, description} = newBug;

      axios.post("https://jsonplaceholder.typicode.com/todos", {title, category, severity, description})
        .then(res => this.bugs = [...this.bugs,  res.data])
        .catch(err => console.log(err)); 
    }
  },
  created(){
    axios.get('https://jsonplaceholder.typicode.com/todos?_limit=5').then(res => this.bugs = res.data).catch(err => console.log(err));
  }
}
</script>

<style>
  #app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
  }

  body, html {
    padding: 0;
    margin: 0;
    width: 100%;
    min-height: 100%; 
  }
  body {
    background-color:aquamarine;
  }

  .btn{
    display: inline-block;
    border: none;
    background: #555;
    color:white;
    padding: 7px 20px;
    cursor: pointer;
  }
  .btn:hover{
    background: #777;
  }

  .container{

  }
  .left{
    float: left;
  }
  .right{
    float: left;
  }

</style>
