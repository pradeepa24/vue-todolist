<template>
  <div class="todo-content">
    <!-- <img alt="Vue logo" src="./assets/logo.png"> -->
    <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo" />
    <button v-if="!showAdd" class="add-list" v-on:click="toggleAdd"><img src="https://img.icons8.com/cotton/2x/add.png" alt="add icon" />Add Task</button>
    <div v-if="showAdd">
    <AddTodo v-on:add-todo="addTodo" />
    <button class="cancel" v-on:click="toggleAdd">Cancel</button>
  </div>
  </div>
</template>

<script>
import Todos from "../components/Todos";
import AddTodo from "../components/AddTodo";
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
      response:{},
      showAdd:false,
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
    },
    toggleAdd(){
     this.showAdd = !this.showAdd;
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

<style scoped>
* {
box-sizing:border-box;
margin:0;
padding: 0;
}

.todo-content{
  margin-top:5%;
  display:flex;
 flex-direction: column;
 justify-content: space-around;
 align-items: center;
 height:auto;
 width:100vw;
}
.add-list img{
  height:5vh;
  width:3vw;
}
.add-list{
  width:10vw;
 display:flex;
 flex-direction: row;
 justify-content: space-around;
 align-items: center;
 background-color: transparent;
 border:transparent;
 cursor:pointer;
 padding:20px;
}
.cancel{
  height:4vh;
  width:10vw;
  background-color:rgba(113, 8, 139, 0.986);
  color:white;
  border:solid 1px rgba(113, 8, 139, 0.986);
  border-radius:8px;
  cursor:pointer;
  font-size:14px;
}
.cancel:hover{
  background-color:white;
  color:rgba(113, 8, 139, 0.986);
}
</style>
