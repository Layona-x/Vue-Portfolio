<script setup>
  import { ref, computed } from 'vue'
import Home from '../App.vue'
import About from '../pages/About.vue'
import NotFound from '../pages/NotFound.vue'

const routes = {
  '/': Home,
  '/about': About
}

const currentPath = ref(window.location.hash)

window.addEventListener('hashchange', () => {
  currentPath.value = window.location.hash
})

const currentView = computed(() => {
  return routes[currentPath.value.slice(1) || '/'] || NotFound
})
 defineProps({ 
   title:{
     type:String,
     require:true
   }
 })
  
</script>
<template>
<nav>
    <h1 style="margin:0;color:black"> {{ title }} </h1>
  <a href="#/home ">Home</a> 
  <a href="#/about">Link-Panel</a>
  <a href="/category">Codes</a>
  <a href="/ekip">Ekip</a> 
  <component :is="currentView" />

</nav>
</template>

<style scope>
*{
  margin:0;
  padding:0;
  box-sizing: border-box; 
}
body{background-color:aliceblue}



nav{
  max-width:600px;
  margin:auto;
  text-align:center;
  justify-content: space-between;
  display:flex; 
  letter-spacing:2px
}

.nav-item{
   justify-content: space-around;
}
a{
  position:relative;
  color:black;
  justify-content:space-around;
  text-decoration: none;
  font-size:18px;
  letter-spacing:0.2px;
}

 a:after{
  content:"";
  background-color:aqua;
  width:0;
  bottom:-10px;
  left:0;
  height:3px;
  position:absolute;
  transition:0.3s
}

a:hover:after{
  width:100%
}

.uptime-form{
  display:flex;
}

input{
  height:50px;
  margin-top:25%;
  width:50%;
  margin-left:17%;
  padding:7px;
  border: 2px solid aqua;
  border-radius: 4px;
}
 input:focus{
  transition:0.3s;
  border: 2px solid aqua;
  border-radius: 4px;
}

.uptime-form .btn-form{
  width:80px;
  height:50px;
  margin-top:25%;
  background-color:#1e90ff;
  border:none;
  color:white;
}

.uptime-form .btn-form:hover{
  background-color:#0095b6;
  transition: 2s
}

@media screen and (min-width: 720px) {
  .uptime-form input{
    margin-top:10%;
  }
  .uptime-form .btn-form{
    margin-top:10%;
  }
}

  </style>