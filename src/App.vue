<template>
  <div id="app">
    <Map />
  </div>
</template>

<script>
import Map from "./components/map.vue";

export default {
  name: "App",
  components: {
    Map,
  },
  data() {
    return {
      center: {
        lat: 40.73061,
        lng: -73.935242,
      },
    };
  },
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
</style>