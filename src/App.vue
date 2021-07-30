<template>
 <div id="app">
   <input type="text" v-model="search" >
   <div v-for="adress in filteredAdresses" :key="adress.id">
     <adress :adress="adress"></adress>
   </div>
   <Map/>
  </div>
</template>

<script>
import Map from './components/map.vue';
import Adress from './components/Adress.vue';

export default {
 name: 'App',
 components: {
   Map,
   Adress
 },
 data() {
   return {
    center:{ 
      lat: 40.730610, 
      lng: -73.935242
    },
      search: '',
      adresses: [
        {
          id: 1,
          title: 'Lille',
        },
        {
          id: 2,
          title: 'Paris',
        },
      ]
   };
 },
 computed: {
   filteredAdresses() {
     return this.adresses.filter(adress => adress.title.toLowerCase().includes(this.search.toLowerCase()))
   }
 }
}
</script>

<style>
  #app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
</style>