<template>
  <div class="home">
    <img alt="Task Image" src="https://entwickler.de/wp-content/uploads/2019/06/just-javascript-task-library-microsoft-900x450.jpg">
    <!-- <HelloWorld msg="Welcome to Your Vue.js App"/> -->
  <div class="title-about">
    <h1>To-Do Lists, Tasks, Reminders & more</h1>
    <div class="title-description">
    <p>Reprogram your brain and automate the important rituals in your life so you have more time for what really matters.</p>
    </div>
  </div>
  </div>
</template>

<script>
// @ is an alias to /src
// import HelloWorld from '@/components/HelloWorld.vue'

export default {
  name: 'home',
  components: {
    // HelloWorld
  }
}
</script>
<style scoped>
.home{
  margin-top:5%;
}
.title-about{
  display:flex;
  flex-direction:column;
  justify-content: space-around;
  align-items: center;
}
.title-description{
  width:30vw;
  color:rgba(113, 8, 139, 0.986);
}
</style>
