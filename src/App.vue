<template>
  <div class="container">
    <Header @toggle-add-task="toggleAddTask" title = 'Task Tracker' :showAddTask="showAddTask"/>
    <router-view :showAddTask = "showAddTask"></router-view>
    <Footer/>
  </div>
  
</template>

<script>

import Header from './components/Header'
import Footer from './components/Footer'


export default {
  name: 'App',
  components: {
    Header,
    Footer
  },
  
  data() {
    return {
      showAddTask: false
    }
  },
  methods:{
    toggleAddTask(){
      this.showAddTask = !this.showAddTask
    }
  }
}
</script>

<style>
  .container{
    border: solid 1px;
    padding: 0px 10px;
  }

  .btn{
    background-color: black;
    color: white;
    padding: 10px;
    cursor: pointer;
    border-radius: 5px;
  }

  .btn-block {
    display: block;
    width: 100%;
    margin-top: 10px;
  }
</style>
