<script setup>
import { ref, onMounted  } from 'vue'
import axios from 'axios'
const props = defineProps(['start', 'day'])
const latitudes = props.day.waypoints.map(wp => wp.latitude)
const longitudes = props.day.waypoints.map(wp => wp.longitude)
const elevations = props.day.waypoints.map(wp => wp.elevation)
const weather = ref([])
const hours = ([8, 10, 12, 14, 16, 18])
const precibitation = ref([0, 0, 0, 0, 0, 0])
const probability = ref([0, 0, 0, 0, 0, 0])
const points = ref([[20, 80], [60, 80], [100, 80], [140, 80], [180, 80], [220, 80]])
const color = (code) => {
  let color = '#ffffff'
  if ([0,1,2].includes(code)) color = '#d7e2ff'
  if ([3,45,48,51,56,61,80].includes(code)) color = '#e4e4e4'
  if ([53,57,63,66,71,73,81,85].includes(code)) color = '#c4c4c4'
  if ([55,65,67,75,77,86].includes(code)) color = '#a4a4a4'
  if ([95].includes(code)) color = '#ff9191'
  if ([96,99].includes(code)) color = '#ff4a4a'
  return color
}
onMounted(async () => {
  const response = await axios.get('https://api.open-meteo.com/v1/forecast?', {
    params: {
      latitude: latitudes.join(','),
      longitude: longitudes.join(','),
      elevation: elevations.join(','),
      hourly: 'temperature_2m,precipitation,precipitation_probability,weather_code',
      timezone: 'Europe/Berlin',
      start_date: props.start,
      end_date: props.start
    }
  })
  weather.value = response.data
  for (let i in weather.value) {
    precibitation.value[i] = weather.value[i]['hourly']['precipitation'][hours[i]] ? (weather.value[i]['hourly']['precipitation'][hours[i]] * 10) : 0
    probability.value[i] = weather.value[i]['hourly']['precipitation_probability'][hours[i]] ? weather.value[i]['hourly']['precipitation_probability'][hours[i]] : 0
    points.value[i][1] = 80 - (weather.value[i]['hourly']['temperature_2m'][hours[i]] * 2)
  }
})
</script>

<template>
  <div class="diagram">
    <svg height="81" width="241" v-if="Object.keys(weather).length > 0">

      <!-- Sky -->

      <rect width="39" height="79" x="1" y="0" :fill="color(weather[0]['hourly']['weather_code'][hours[0]])"></rect>
      <rect width="39" height="79" x="41" y="0" :fill="color(weather[1]['hourly']['weather_code'][hours[1]])"></rect>
      <rect width="39" height="79" x="81" y="0" :fill="color(weather[2]['hourly']['weather_code'][hours[2]])"></rect>
      <rect width="39" height="79" x="121" y="0" :fill="color(weather[3]['hourly']['weather_code'][hours[3]])"></rect>
      <rect width="39" height="79" x="161" y="0" :fill="color(weather[4]['hourly']['weather_code'][hours[4]])"></rect>
      <rect width="39" height="79" x="201" y="0" :fill="color(weather[5]['hourly']['weather_code'][hours[5]])"></rect>

      <!-- Precibitation -->

      <rect transform="rotate(-90, 1, 79)" :width="precibitation[0]" height="39" x="1" y="79" fill="#88b4ff"></rect>
      <rect transform="rotate(-90, 41, 79)" :width="precibitation[1]" height="39" x="41" y="79" fill="#88b4ff"></rect>
      <rect transform="rotate(-90, 81, 79)" :width="precibitation[2]" height="39" x="81" y="79" fill="#88b4ff"></rect>
      <rect transform="rotate(-90, 121, 79)" :width="precibitation[3]" height="39" x="121" y="79" fill="#88b4ff"></rect>
      <rect transform="rotate(-90, 161, 79)" :width="precibitation[4]" height="39" x="161" y="79" fill="#88b4ff"></rect>
      <rect transform="rotate(-90, 201, 79)" :width="precibitation[5]" height="39" x="201" y="79" fill="#88b4ff"></rect>

      <!-- Grid -->

      <rect width="241" height="1" x="0" y="0" fill="#ffffff"></rect>
      <rect width="241" height="1" x="0" y="20" fill="#ffffff"></rect> 
      <rect width="241" height="1" x="0" y="40" fill="#ffffff"></rect>
      <rect width="241" height="1" x="0" y="60" fill="#ffffff"></rect>
      <rect width="241" height="1" x="0" y="80" fill="#ffffff"></rect>

      <rect width="1" height="80" x="0" y="0" fill="#ffffff"></rect>
      <rect width="1" height="80" x="40" y="0" fill="#ffffff"></rect>
      <rect width="1" height="80" x="80" y="0" fill="#ffffff"></rect>
      <rect width="1" height="80" x="80" y="0" fill="#ffffff"></rect>
      <rect width="1" height="80" x="120" y="0" fill="#ffffff"></rect>
      <rect width="1" height="80" x="160" y="0" fill="#ffffff"></rect>
      <rect width="1" height="80" x="200" y="0" fill="#ffffff"></rect>
      <rect width="1" height="80" x="240" y="0" fill="#ffffff"></rect>

      <!-- Temperature -->

      <polyline :points="points.map(point => point.join(',')).join(' ')" stroke-linecap="round" stroke-linejoin="round" style="fill:none;stroke:#444444;stroke-width:4"></polyline>

    </svg>

  </div>

  <!-- Probability -->

  <div class="probability">
    <div>{{ probability[0] }}%</div>
    <div>{{ probability[1] }}%</div>
    <div>{{ probability[2] }}%</div>
    <div>{{ probability[3] }}%</div>
    <div>{{ probability[4] }}%</div>
    <div>{{ probability[5] }}%</div>
  </div>

</template>

<style lang="css">
.diagram {
  padding: 0;
}
.probability {
  padding: 0;
  display: flex;
  > div {
    min-width: 40px;
    height: 16px;
  }
}
</style>