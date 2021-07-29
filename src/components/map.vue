<template>
  <body>
    <div class="map--container">
      <h2>Mais où se trouve donc Wilson ?</h2>
      <p>Affiche les deux adresses de l'agence Ylly : Lille et Paris ! </p>
      <p>Créer une barre de recherche pour sélectionner la bonne agence. </p>
       <l-map
        :center="center"
        :zoom="zoom"
        class="map"
        ref="map"
        @update:zoom="zoomUpdated"
        @update:center="centerUpdated"
      >
        <l-tile-layer
          :url="url"
   >
        </l-tile-layer>
      </l-map>
    </div>

  </body>
</template>

<script>
  import { LMap, LTileLayer } from 'vue2-leaflet';
import 'leaflet/dist/leaflet.css';

export default {
 components: {
   LMap,
   LTileLayer
 },
 data () {
   return {
     url: 'https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png',
     center: [ 49.1193089, 6.1757156 ],
     zoom: 12,
   }
 },
 methods: {
   zoomUpdated (zoom) {
     this.zoom = zoom;
     console.log(this.markers)
   },
   centerUpdated (center) {
     this.center = center;
   }
 }
}
</script>

<style>

  body {
    background: #4D6A79;
  }
  .map--container {
    text-align: center;
    color: whitesmoke;
  }

 .map {
   position: absolute;
   width: 100%;
   height: 100%;
   overflow :hidden;
 }
</style>