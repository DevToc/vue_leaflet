<script setup>
import {ref} from 'vue'

const name = ref("")
const description = ref("")
const latitude = ref("")
const longitude = ref("")

const isEmpty = () => {
  if(name.value==="" || description.value==="" || latitude.value==="" || longitude.value===""){
    return true;
  }
  return false;
}

const handleSubmit = () => {
  alert("Dd")
}

</script>

<template>
  <div class="info-form p-4">
    <form @submit.prevent="handleSubmit">
      <div class="form-item">
        <label for="">Location Name:</label>
        <input class="form-control" type="text" v-model="name" placeholder="name" />
      </div>
      <div class="form-item">
        <label for="">Description:</label>
        <textarea class="form-control" name="" id="" v-model="description" cols="30" rows="10"></textarea>
      </div>
      <div class="form-item">
        <label for="">Latitude: </label>
        <input class="form-control" type="number" v-model="latitude" pattern="^\d*(\.\d{0,2})?$" step="0.01" placeholder="" />
      </div>
      <div class="form-item">
        <label for="">Longitude: </label>
        <input class="form-control" type="number" v-model="longitude" pattern="^\d*(\.\d{0,2})?$" step="0.01" placeholder="" />
      </div>
      <button class="btn btn-primary form-control" :disabled="isEmpty()">Submit</button>
    </form>
  </div>
</template>
