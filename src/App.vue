<template>
  <div id="app">
    <header id="header">ToDo's</header>
    <form v-on:submit.prevent="saveNewTodo">
      <label id="text-box" for="new-todo">Add to list:</label>
      <input id="new-todo" type="text" v-model="newTodo">
      <input type="submit" value="save">
    </form>
    <ul>
      <li id="list" v-for="(item, index) in todos" v-bind:key="index">
        <span>{{item.name}}</span>
        <span v-if="item.completed">Complete!</span>
        <button id="button" v-if="!item.completed" v-on:click="finishTodo(index)">Complete task</button>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data(){
    return{
      todos:[
        {name: "Shopping", completed: false},
        {name: "Clean house", completed: false},
        {name: "Feed cats", completed: false},
        {name: "Buy Christmas presents!", completed: false},
        {name: "WIN THE LOTTERY", completed: false}
      ],
      newTodo: ""
    }
  },
  methods: {
    saveNewTodo: function(){
      this.todos.push({
        name: this.newTodo,
        completed: false
      });
      this.newTodo = "";
    },
    finishTodo: function(index){
      this.todos[index].completed = true;
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  color: #2c3e50;
  margin-top: 20px;
}
#header {
  margin-left: 20px;
  margin-bottom:30px;
  font-family: Avenir, Helvetica;
  font-style: bold;
  font-size: 40px;
  color: black
}
#list {
  padding-top: 20px;
}
#button {
  margin-left: 10px;
}
#text-box {
  margin-left: 25px;
}
</style>
