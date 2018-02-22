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

<style lang="scss">
$guide-color: #bbbbbb;

$circle-position: 10%;
$circle-box-size: 85vh 85vh;
$circle-gradient: $guide-color 90%, $primary-color 91%, $primary-color 94%, transparent 95%;
$mask-size: 100% 82vh;
$dash-size: 4vh 15vh;

#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  padding: 0 0 1px;
  margin: 0;
  color: white;

  background:
    radial-gradient(circle closest-side at 50% 100-$circle-position, $circle-gradient),
    radial-gradient(circle closest-side at 50% 0+$circle-position, $circle-gradient),
    linear-gradient($primary-color, $primary-color),
    linear-gradient($primary-color, $primary-color),
    linear-gradient($primary-color 10%, $guide-color 11%, $guide-color 79%, $primary-color 80%);
  background-repeat: no-repeat, no-repeat, no-repeat, no-repeat, repeat-y;
  background-position: 50% top, 50% bottom, top, bottom, 50% 20vh;
  background-size: $circle-box-size, $circle-box-size, $mask-size, $mask-size, $dash-size;
}
* {
  border:0;
  margin:0;
}
body{
  background-color:$primary-color;
}
</style>
