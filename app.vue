
<template>
  <div style="height:50vh; width:100vw">
    <LMap
      ref="map"
      :zoom="zoom"
      :center="[15.0954004,-90.3994991]"
    >
      <LTileLayer
        url="https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png"
        attribution="&amp;copy; <a href=&quot;https://www.openstreetmap.org/&quot;>OpenStreetMap</a> contributors"
        layer-type="base"
        name="OpenStreetMap"
      />

      <LCircleMarker ref="circles"  v-for="(markers, location) in station" :name="location" :lat-lng=markers.coord :radius="15" :fill-opacity="0.6" :fill-color="markers.color" :color="markers.color" v-on:click="circleClick(location)" />
      
    </LMap>


    <div class="container">
      <select class="mx-auto mx-3" v-model="selectedLocation" @change="updateMarkerColor(selectedLocation)">
        <option v-for="(markers, location) in station" :value="location">{{location}}</option>
      </select>
      <h1 class="text-5xl text-center">{{ selectedLocation }}</h1>
    </div>

  </div>
</template>

<script setup>
import { ref, reactive } from 'vue'
const circles = ref([])
const zoom = ref(10)
const station = reactive({
  'Cubulco': {coord: [15.1057891,-90.645919], color: 'red'},
  'Granados': {coord: [14.917233,-90.5280519], color: '#3388ff'},
  'Purulhá': {coord: [15.237121,-90.2469779], color: '#3388ff'},
  'Rabinal': {coord: [15.0855182,-90.497818], color: '#3388ff'},
  'Salamá': {coord: [15.1026613,-90.3258347], color: '#3388ff'},
  'San Jerónimo': {coord: [15.062499,-90.245862], color: '#3388ff'},
  'San Miguel Chica': {coord: [15.0954004,-90.3994991], color: '#3388ff'},
  'Santa Cruz El Chol': {coord: [14.9612142,-90.4940415], color: '#3388ff'}
})
const selectedLocation = ref('Cubulco')


function updateMarkerColor(n) {
  console.log('update marker!')
  circles.value.forEach((el) => {
    if(el.name === n){
      station[n].color = 'red'
    } else {
      station[el.name].color = '#3388ff'
  }})
}

function circleClick(n) {
  selectedLocation.value = n
  updateMarkerColor(n)
}


</script>

<style>
body {
  margin: 0;
}
</style>
