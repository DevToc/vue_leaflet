<script setup>
import InfoForm from "./components/InfoForm.vue";
import MapView from "./components/MapView.vue";

const handleSubmit = (e) => {
  console.log(e)
}

</script>

<template>
  <div class="container">
    <h1 class="my-4 text-center">Test</h1>
    <div class="row">
      <div class="col-4">
        <InfoForm />
      </div>
      <div class="col-8">
        <MapView></MapView>
      </div>
    </div>
  </div>
</template>
