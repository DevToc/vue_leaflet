<script setup>
import { ref } from "vue";
import { defineEmits } from "vue";

const emit = defineEmits(["handleSubmit"]);

const name = ref("");
const description = ref("");
const latitude = ref("");
const longitude = ref("");

const isEmpty = () => {
  if (
    name.value === "" ||
    description.value === "" ||
    latitude.value === "" ||
    longitude.value === ""
  ) {
    return true;
  }
  return false;
};

const handleSubmit = () => {
  emit("handleSubmit", {
    name: name.value,
    description: description.value,
    latitude: latitude.value,
    longitude: longitude.value,
  });
};
</script>

<template>
  <div class="info-form">
    <form @submit.prevent="handleSubmit">
      <h3 class="text-center text-info">Information</h3>
      <div class="content">
        <div class="form-item">
          <label for="name">Location Name *:</label>
          <input class="form-control" type="text" v-model="name" />
        </div>
        <div class="form-item">
          <label for="description">Description *:</label>
          <textarea
            class="form-control"
            v-model="description"
            cols="30"
            rows="5"
          ></textarea>
        </div>
        <div class="form-item">
          <label for="Latitude">Latitude *: </label>
          <input
            class="form-control"
            type="number"
            v-model="latitude"
            pattern="^\d*(\.\d{0,2})?$"
            step="0.01"
          />
        </div>
        <div class="form-item">
          <label for="Longitude">Longitude *: </label>
          <input
            class="form-control"
            type="number"
            v-model="longitude"
            pattern="^\d*(\.\d{0,2})?$"
            step="0.01"
          />
        </div>
        <button class="btn btn-primary form-control" :disabled="isEmpty()">
          Submit
        </button>
      </div>
    </form>
  </div>
</template>

<style scoped>
.form-item {
  margin-bottom: 20px;
}
@media (max-width: 800px) {
  .content {
    display: flex;
    flex-wrap: wrap;
    justify-content: space-between;
  }
  .form-item {
    width: 48%;
  }
  textarea {
    height: 1rem;
  }
  .info-form {
    margin-bottom: 30px;
  }
}
</style>
