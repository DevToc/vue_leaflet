<script setup>
import { defineProps, ref } from "vue";
import { LMap, LTileLayer, LMarker } from "@vue-leaflet/vue-leaflet";

import "leaflet/dist/leaflet.css";

const props = defineProps(["information"]);
const tooltip = ref(false);
const zoom = 6;

const handleMarkerClick = () => {
  tooltip.value = true;
  setTimeout(() => {
    tooltip.value = false;
  }, 1000);
};
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
        v-if="information.latitude"
        :lat-lng="[
          information.latitude ? information.latitude : 47.41322,
          information.longitude ? information.longitude : -1.219482,
        ]"
        @click="handleMarkerClick"
      >
      </l-marker>
      <div class="tooltip-wrapper" v-if="tooltip">
        <h4>name: {{ props.information.name }}</h4>
        <p>detail:{{ props.information.description }}</p>
      </div>
    </l-map>
  </div>
</template>
<style scoped>
.tooltip-wrapper {
  position: absolute;
  text-align: left;
  top: 100px;
  left: 100px;
  padding: 10px;
  color: #0dcaf0;
  background-color: white;
  border-radius: 20px;
  z-index: 1000;
}
.map-wrapper {
  height: 100%;
}
@media (max-width: 800px) {
  .map-wrapper {
    height: 400px;
  }
}
</style>
