<template>
  <body>
    <div class="map--container">
      <h2>VueJs Map</h2>

      <input type="text" v-model="search" placeholder="Search..." />
      <div v-for="adress in filteredAdresses" :key="adress.id">
        <adress :adress="adress"></adress>
      </div>
      <l-map
        :center="center"
        :zoom="zoom"
        class="map"
        ref="map"
        @update:zoom="zoomUpdated"
        @update:center="centerUpdated"
      >
        <l-tile-layer :url="url"> </l-tile-layer>
        <agence v-for="marker in markers" :key="marker.id" :marker="marker">
        </agence>
      </l-map>
    </div>
  </body>
</template>

<script>
import { LMap, LTileLayer } from "vue2-leaflet";
import Agence from "./agence.vue";
import "leaflet/dist/leaflet.css";

import Adress from "./Adress.vue";

export default {
  components: {
    LMap,
    LTileLayer,
    Agence,
    Adress,
  },
  data() {
    return {
      url: "https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png",
      center: [50.635342, 3.05857],
      zoom: 6,
      search: "",
      adresses: [
        {
          id: 1,
          town: "Lille",
          latitude: 50.635342,
          longitude: 3.05857
        },
        {
          id: 2,
          town: "Paris",
          latitude: 48.813843,
          longitude: 2.392828
        },
      ],

      markers: [
        {
          id: 1,
          imageUrl: "https://img.icons8.com/doodle/48/000000/pinguin.png",
          coordinates: [50.635342, 3.05857],
        }, // Lille Ylly
        {
          id: 2,
          imageUrl: "https://img.icons8.com/doodle/48/000000/home--v1.png",
          coordinates: [48.813843, 2.392828],
        }, // Paris Ylly
      ],
    };
  },
  methods: {
    zoomUpdated(zoom) {
      this.zoom = zoom;
      console.log(this.markers);
    },
    centerUpdated(center) {
      this.center = center;
    },
  },
   computed: {
   filteredAdresses() {
     return this.adresses.filter(adress => adress.town.toLowerCase().includes(this.search.toLowerCase()))
   }
 }
};
</script>

<style>
body {
  background: #4d6a79;
}
.map--container {
  text-align: center;
  color: whitesmoke;
}

.map {
  position: absolute;
  width: 100%;
  height: 100%;
  border: 0.2rem solid white;
}
</style>
