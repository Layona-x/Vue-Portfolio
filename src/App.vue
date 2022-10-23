<script setup>
  import Navbar from './components/Navbar.vue'
  import Profile from './components/Profile.vue'
</script>

<script>
  import axios from 'axios'
  let lanyardUrl = "https://api.lanyard.rest/v1/users/920315243106795570"
export default {
  data () {
    return {
      lanyard:null,
      info:{
        durum:null,
        username:null,
        avatar:null,
        discriminator:null,
        id:null,
      },
    }
  },
  created: function(){
    axios.get(lanyardUrl).then((res)=>{
    this.lanyard = res.data.data
    this.info.username = this.lanyard.discord_user.username
    console.log(this.lanyard)
    })
  }
}
</script>
<template>
<Navbar title="Decs"/>
<h1 id="profile_username"> {{ info.username }} </h1>
</template>