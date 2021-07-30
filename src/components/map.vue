<template>
  <body>
    <div class="map--container">
      <h2>VueJs Map</h2>

      <select
        name="agency"
        id="agency-select"
        v-model="selectAgency"
      >
        <option value="">-- Please choose an agency --</option>
        <option v-for="adress in adresses" :key="adress.id" v-bind:value="adress.id">{{ adress.agency }}</option>
      </select>
      <p>
      {{ selectAgency }}
</p>
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
import Agence from "./AgenceIcons.vue";
import "leaflet/dist/leaflet.css";

import adressesData from "../adresses.json";

export default {
  components: {
    LMap,
    LTileLayer,
    Agence,

  },
  data() {
    let markers = Array();
    adressesData.adresses.forEach((adress) => {
      markers.push({
        id: adress.id,
        coordinates: [adress.latitude, adress.longitude],
        imageUrl: adress.imageUrl,
      });
    });

    return {
      url: "https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png",
      center: [50.635342, 3.05857],
      zoom: 6,
      search: "",
      adresses: adressesData.adresses,
      markers: markers,
      selectAgency: ''
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
      return this.adresses.filter((adress) =>
        adress.agency.toLowerCase().includes(this.search.toLowerCase())
      );
    },
  },
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
