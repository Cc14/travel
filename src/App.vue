<template>
  <div id="app">
    <keep-alive exclude="Detail">
    <router-view/>
    
    </keep-alive>
    
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      show: true
    };
  }
};
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  background: #f5f5f5
}

</style>
