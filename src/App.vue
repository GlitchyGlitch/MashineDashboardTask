<template>
  <header class="top-bar"><h3>Machine dashboard</h3></header>
  <div class="fleet-app">
    <FleetManager />
  </div>
</template>

<script>
import FleetManager from "./components/FleetManager.vue";
export default {
  name: "App",
  components: {
    FleetManager,
  },
};
</script>

<style>
body {
  margin: 0;
}
.fleet-app,
.top-bar {
  padding: 0;
  margin: 0;
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}
.top-bar h3 {
  margin: 0;
}
.top-bar {
  padding: 20px 30px;
  color: #fff;
  background-color: #2c3e50;
}
</style>
