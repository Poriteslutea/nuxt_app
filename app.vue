
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

      <LCircleMarker v-for="stat in station" :name="stat.location" :lat-lng=stat.coord :radius="15" :fill-opacity="0.6" v-on:click="circleClick" />
    </LMap>

    <h1 class="text-5xl text-center">{{ stat_name }}</h1>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const zoom = ref(10)
const stat_name = ref('')
const stat_coord = ref('')
const station = ref([
{
  location: 'Cubulco', 
  coord: [15.1057891,-90.645919]
}, 
{
  location: 'Granados', 
  coord: [14.917233,-90.5280519]
}, 
{
  location: 'Purulhá', 
  coord: [15.237121,-90.2469779]
}, 
{
  location: 'Rabinal' , 
  coord: [15.0855182,-90.497818]
}, 
{
  location: 'Salamá' , 
  coord: [15.1026613,-90.3258347]
}, 
{
  location: 'San Jerónimo', 
  coord: [15.062499,-90.245862]
}, 
{
  location: 'San Miguel Chica' , 
  coord: [15.0954004,-90.3994991]
}, 
{
  location: 'Santa Cruz El Chol', 
  coord: [14.9612142,-90.4940415]
}
])

var clicked

function circleClick(e) {
  console.log(e.sourceTarget.options.name)
  station.value.forEach(st => {
    if(st.coord[0] == e.target._latlng.lat && st.coord[1] == e.target._latlng.lng){
      stat_name.value = st.location
    }
  })
  if (clicked) {
    clicked.setStyle({fillColor: '#3388ff', fillOpacity: 0.6, color:'#3388ff'});
  }
  e.target.setStyle({fillColor: 'red', fillOpacity: 0.6, color: 'red'});
  clicked = e.target;
}


watch(stat_name, (sn) => {

})


</script>

<style>
body {
  margin: 0;
}
</style>
