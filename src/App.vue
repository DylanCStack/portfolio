<template>
  <div id="app">
    <router-view/>
  </div>
</template>

<script>
export default {
  name: 'app',
};
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  padding: 0;
  margin: 0;
  color: white;

  background:
    radial-gradient(circle closest-side at 50% 70%, #bbb 90%, black 91%, black 94%, transparent 95%),
    radial-gradient(circle closest-side at 50% 30%, #bbb 90%, black 91%, black 94%, transparent 95%),
    linear-gradient(#000, #000),
    linear-gradient(#000, #000),
    linear-gradient(#000 10%, #bbb 11%, #bbb 79%, #000 80%);
  background-repeat: no-repeat, no-repeat, no-repeat, no-repeat, repeat-y;
  background-position: 50% top, 50% bottom, top, bottom, 50% 30vh;
  background-size: 60vh 60vh, 60vh 60vh, 100% 60vh, 100% 60vh, 4vh 15vh;
}
* {
  border:0;
  margin:0;
}
body{
  background-color:black;
  color:#aaa;
}
</style>
