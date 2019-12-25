<template>
  <div class="add-form">
    <form  @submit="addTodo">
      <input type="text" name="title" placeholder="Add Todo.." v-model="title"/>
      <input type="submit" value="Submit" class="btn" />
    </form>
  </div>
</template>
<script>
// import uuid from 'uuid';
export default {
  name: "AddTodo",
  data(){
      return {
          title:''
          }
      },
  methods:{
      addTodo(e) {
          e.preventDefault();
       const newTodo = {
        //    id:uuid.v4(),
           title:this.title,
           completed:false
           }
           this.$emit('add-todo',newTodo);
           this.title = "";
      }
    }
};
</script>
<style scoped>
.add-form{
  padding:20px;
  width:100vw;
}
form {
  display: flex;
  height:10vh;
  padding:10px;
  width:100%;
}
.btn {
  display: inline-block;
  border: none;
  background: #555;
  color: #fff;
  padding: 7px 20px;
  cursor: pointer;
}
.btn:hover {
 background-color:white;
  color:rgba(113, 8, 139, 0.986);
}
input[type="text"] {
  height:5vh;
  flex: 10;
  padding: 5px;
  border-top-left-radius:8px;
  border-bottom-left-radius:8px;
}
input[type="submit"] {
  flex: 2;
  height:6.55vh;
   border-top-right-radius:8px;
  border-bottom-right-radius:8px;
   background-color:rgba(113, 8, 139, 0.986);
    border:solid 1px rgba(113, 8, 139, 0.986);
}
</style>