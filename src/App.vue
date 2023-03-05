
<template>
  <div>
    <div>
      <a href='#/todo'>ToDo</a>
    </div>
  </div>
  <component :is = currentView />
</template>

<script>
import ToDo from './components/ToDo.vue'
const routes ={
  '/todo': ToDo
}
  export default{
    data(){
      return {
        currentPath: window.location.hash
      }
    },
    computed:{
      currentView(){
        return routes[this.currentPath.slice(1) || '/']
      }
    },
    mounted(){
      window.addEventListener('hashchange',()=>{
        this.currentPath = window.location.hash
      })
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
</style>
