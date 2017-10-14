<template>
  <div id="app">
   
    <router-view class="content"></router-view>
  </div>
</template>

<script>
    export default {
        name: 'app'
    }
</script>

<style>
    #app {
        min-height: 100%;
        position: relative
    }
    
    * {
        margin: 0;
        padding: 0;
        list-style: none;
    }
    
    a {
        color: black;
        text-decoration: none
    }
    
    .content {
        min-height: 100%;
    }
</style>