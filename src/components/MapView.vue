<script setup>
import { defineProps } from "vue";
import "leaflet/dist/leaflet.css";
import { LMap, LTileLayer, LMarker } from "@vue-leaflet/vue-leaflet";
const zoom = 6;

 defineProps(["information"]);
// watch(
//   () => props.information,
//   (newInfo, old) => {
//     console.log(newInfo, old);
//   }
// );
</script>

<template>
  <div class="map-wrapper w-100">
    <l-map
      ref="map"
      v-model:zoom="zoom"
      :center="[
        information.latitude ? information.latitude : 47.41322,
        information.longitude ? information.longitude : -1.219482,
      ]"
    >
      <l-tile-layer
        url="https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png"
        layer-type="base"
        name="OpenStreetMap"
      ></l-tile-layer>
      <l-marker
        :lat-lng="[
          information.latitude ? information.latitude : 47.41322,
          information.longitude ? information.longitude : -1.219482,
        ]"
      >
      </l-marker>
    </l-map>
  </div>
</template>
<style scoped>
.map-wrapper {
  height: 100%;
}
@media (max-width: 800px) {
  .map-wrapper {
    height: 400px;
  }
}
</style>
