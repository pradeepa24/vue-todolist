<template>
  <div id="app">
    <header>
        <router-link to="/"><img src="https://www.freeiconspng.com/uploads/tasks-icon-32.png" alt="tasker" /></router-link>
      <div id="nav">
        <router-link to="/">Home</router-link> 
        <router-link to="/about">About </router-link>
        <router-link to="/todoList">Todo List</router-link>
      </div>
    </header>
    <router-view/>
  </div>
</template>

<style>
body{
  padding:0;
  margin:0;
  font-family:Arial, Helvetica, sans-serif;
line-height:1.4;
}

#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
header{
   position: fixed;
  top: 0;
  width: 100%;
  background-color:rgba(113, 8, 139, 0.986);
   display:flex;
  flex-direction:row;
  justify-content: space-between;
  align-items: center;
  padding:0 50px 0 50px;
  height:8vh;
}
#nav {
  /* padding: 30px; */
  display:flex;
  flex-direction:row;
  justify-content: space-around;
  align-items: center;
  width:40vw;
  padding: 0 30px;
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
}
header a img{
  height:5vh;
  width:4vw;
}
#nav a {
  color: white;
  text-decoration:none;
}
#nav a:hover{
  background-color:whitesmoke;
  border:1px solid whitesmoke;
  color:black;
  border-radius:5px;
}
/* .router-link-exact-active */
</style>
