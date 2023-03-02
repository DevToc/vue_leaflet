<script setup>
import { ref } from "vue";
import InfoForm from "./components/InfoForm.vue";
import MapView from "./components/MapView.vue";

const information = ref({});

const handleSubmit = (info) => {
  information.value = info;
};
</script>

<template>
  <div class="main-wrapper">
    <h1 class="my-4 text-center text-danger">Test Project</h1>
    <div class="content">
      <div class="info-view">
        <InfoForm @handleSubmit="handleSubmit" />
      </div>
      <div class="map-view">
        <MapView :information="information"></MapView>
      </div>
    </div>
  </div>
</template>

<style scoped>
.content {
  display: flex;
  justify-content: space-between;
}
.main-wrapper {
  padding: 2rem 10% !important;
}
.info-view {
  width: 33%;
}
.map-view {
  width: 66%;
}

@media (max-width: 1250px) {
  .main-wrapper {
    padding: 2rem 5% !important;
  }
}
@media (max-width: 800px) {
  .main-wrapper {
    padding: 2rem 5% !important;
  }
  .content {
    flex-direction: column;
  }
  .info-view {
    width: 100%;
  }
  .map-view {
    width: 100%;
  }
}
</style>
