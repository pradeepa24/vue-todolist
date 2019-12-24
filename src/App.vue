<template>
  <div>
    <AddTodo v-on:add-todo="addTodo" />
    <!-- <img alt="Vue logo" src="./assets/logo.png"> -->
    <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo" />
  </div>
</template>

<script>
import Todos from "./components/Todos";
import AddTodo from "./components/AddTodo";
import axios from "axios";
export default {
  name: "app",
  components: {
    Todos,
    AddTodo
  },
  data() {
    return {
      todos: [],
      errors:{},
      response:{}
    };
  },
  methods: {
    deleteTodo(id) {
      axios.delete("https://jsonplaceholder.typicode.com/todos/"+id)
           .then(res => {
         // console.log(res);
         this.response = res;
          this.todos = this.todos.filter(todo => todo.id !== id)
          })
           .catch(err => this.errors = err);
      this.todos = this.todos.filter(todo => todo.id !== id);
    },
    addTodo(newTodo) {
      const { title, completed } = newTodo;
      axios.post("https://jsonplaceholder.typicode.com/todos",{
        title,
        completed
        })
        .then(res => {
          this.response = res;
        //  console.log(res);
          this.todos = [...this.todos, newTodo]
          })
        .catch(err => this.errors = err);
    }
  },
  created() {
    axios
      .get("https://jsonplaceholder.typicode.com/todos?_limit=5")
      .then(res => this.todos = res.data)
      .catch(err => this.errors = err );
  }
};
</script>
* {
box-sizing:border-box;
margin:0;
padding: 0;
}
body {
font-family:Arial, Helvetica, sans-serif;
line-height:1.4;
}

<style>
</style>
