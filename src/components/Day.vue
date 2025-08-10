<script setup>
import { ref, onMounted  } from 'vue'
import axios from 'axios'
const props = defineProps(['start', 'day'])
const latitudes = props.day.waypoints.map(wp => wp.latitude)
const longitudes = props.day.waypoints.map(wp => wp.longitude)
const elevations = props.day.waypoints.map(wp => wp.elevation)
const weather = ref([])
const rain = ref([0, 0, 0, 0, 0, 0])
const points = ref([[10, 80], [30, 80], [50, 80], [70, 80], [90, 80], [110, 80]])
const hours = ([8, 10, 12, 14, 16, 18])
const getCodeColor = (code) => {
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
      hourly: 'temperature_2m,rain,weather_code',
      timezone: 'Europe/Berlin',
      start_date: props.start,
      end_date: props.start
    }
  })
  let rainAmount = 0
  weather.value = response.data
  for (let i in weather.value) {
    rain.value[i] = weather.value[i]['hourly']['rain'][hours[i]] ? (weather.value[i]['hourly']['rain'][hours[i]] * 2) - 1 : 0
    if (weather.value[i]['hourly']['rain'][hours[i]] > rainAmount) {
      rainAmount = weather.value[i]['hourly']['rain'][hours[i]]
    }
    points.value[i][1] = 80 - (weather.value[i]['hourly']['temperature_2m'][hours[i]] * 2)
  }
  console.log(rainAmount)
})
</script>

<template>
    <svg height="81" width="121" v-if="Object.keys(weather).length > 0">

            <!-- Sky -->

            <rect width="19" height="79" x="1" y="0" :fill="getCodeColor(weather[0]['hourly']['weather_code'][hours[0]])"></rect>
            <rect width="19" height="79" x="21" y="0" :fill="getCodeColor(weather[1]['hourly']['weather_code'][hours[1]])"></rect>
            <rect width="19" height="79" x="41" y="0" :fill="getCodeColor(weather[2]['hourly']['weather_code'][hours[2]])"></rect>
            <rect width="19" height="79" x="61" y="0" :fill="getCodeColor(weather[3]['hourly']['weather_code'][hours[3]])"></rect>
            <rect width="19" height="79" x="81" y="0" :fill="getCodeColor(weather[4]['hourly']['weather_code'][hours[4]])"></rect>
            <rect width="19" height="79" x="101" y="0" :fill="getCodeColor(weather[5]['hourly']['weather_code'][hours[5]])"></rect>

            <!-- Rain -->

            <rect transform="rotate(-90, 1, 79)" :width="rain[0]" height="19" x="1" y="79" fill="#88b4ff"></rect>
            <rect transform="rotate(-90, 21, 79)" :width="rain[1]" height="19" x="21" y="79" fill="#88b4ff"></rect>
            <rect transform="rotate(-90, 41, 79)" :width="rain[2]" height="19" x="41" y="79" fill="#88b4ff"></rect>
            <rect transform="rotate(-90, 61, 79)" :width="rain[3]" height="19" x="61" y="79" fill="#88b4ff"></rect>
            <rect transform="rotate(-90, 81, 79)" :width="rain[4]" height="19" x="81" y="79" fill="#88b4ff"></rect>
            <rect transform="rotate(-90, 101, 79)" :width="rain[5]" height="19" x="101" y="79" fill="#88b4ff"></rect>

            <!-- Grid -->

            <rect width="121" height="1" x="0" y="0" fill="#ffffff"></rect>
            <rect width="121" height="1" x="0" y="20" fill="#ffffff"></rect> 
            <rect width="121" height="1" x="0" y="40" fill="#ffffff"></rect>
            <rect width="121" height="1" x="0" y="60" fill="#ffffff"></rect>
            <rect width="121" height="1" x="0" y="80" fill="#ffffff"></rect>

            <rect width="1" height="80" x="0" y="0" fill="#ffffff"></rect>
            <rect width="1" height="80" x="20" y="0" fill="#ffffff"></rect>
            <rect width="1" height="80" x="40" y="0" fill="#ffffff"></rect>
            <rect width="1" height="80" x="60" y="0" fill="#ffffff"></rect>
            <rect width="1" height="80" x="80" y="0" fill="#ffffff"></rect>
            <rect width="1" height="80" x="100" y="0" fill="#ffffff"></rect>
            <rect width="1" height="80" x="120" y="0" fill="#ffffff"></rect>

            <!-- Temperature -->

            <polyline :points="points.map(point => point.join(',')).join(' ')" stroke-linecap="round" stroke-linejoin="round" style="fill:none;stroke:#444444;stroke-width:6"></polyline>

        </svg>
</template>
