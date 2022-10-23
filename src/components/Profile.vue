<script setup>
defineProps({
  username:{
    type:String,
    require:true
  }
})
</script>
<template>
  <div class="profile">
    <h1>
   {{ username }}
    </h1>
  </div>
    
</template>

<style scope>
  .profile{

    color:green;
  
    
  }
  </style>