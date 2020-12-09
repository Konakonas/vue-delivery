<template>
  <div id="app">
    <Home/>
  </div>
</template>

<script>
  import Home from './components/Home'
  export default {
    components: {
        Home
    }
}
</script>

<style>
* {box-sizing: border-box;}
body {background: #f69a73;}
.decor {
  position: relative;
  max-width: 600px;
  margin: 50px auto 0;
  background: white;
  border-radius: 30px;
}
</style>
