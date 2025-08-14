<script setup>
import { ref } from 'vue'
import Day from './components/Day.vue'
const departures = ref([
  '2025-08-18',
  '2025-08-19',
  '2025-08-20',
  '2025-08-21',
  '2025-08-22',
  '2025-08-23',
  '2025-08-24'
]);
const days = ref([
  {
    id: 1,
    waypoints: [
      { id: 1, latitude: '52.26', longitude: '9.75', elevation: '68' },
      { id: 2, latitude: '51.42', longitude: '9.89', elevation: '191' },
      { id: 3, latitude: '50.57', longitude: '9.71', elevation: '321' },
      { id: 4, latitude: '49.76', longitude: '10.10', elevation: '312' },
      { id: 5, latitude: '48.84', longitude: '10.19', elevation: '640' },
      { id: 6, latitude: '47.92', longitude: '9.75', elevation: '585' },
    ]
  },
  {
    id: 2,
    waypoints: [
      { id: 1, latitude: '47.92', longitude: '9.75', elevation: '585' },
      { id: 2, latitude: '47.46', longitude: '9.37', elevation: '585' },
      { id: 3, latitude: '47.20', longitude: '9.35', elevation: '1214' },
      { id: 4, latitude: '46.88', longitude: '9.87', elevation: '1118' },
      { id: 5, latitude: '46.53', longitude: '10.13', elevation: '1819' },
      { id: 6, latitude: '46.62', longitude: '9.74', elevation: '1363' },
    ]
  },
  {
    id: 3,
    waypoints: [
      { id: 1, latitude: '46.62', longitude: '9.74', elevation: '1363' },
      { id: 2, latitude: '46.47', longitude: '9.72', elevation: '2284' },
      { id: 3, latitude: '46.33', longitude: '9.51', elevation: '705' },
      { id: 4, latitude: '46.54', longitude: '9.24', elevation: '1581' },
      { id: 5, latitude: '46.29', longitude: '9.18', elevation: '408' },
      { id: 6, latitude: '46.52', longitude: '8.93', elevation: '891' },
    ]
  },
  {
    id: 4,
    waypoints: [
      { id: 1, latitude: '46.52', longitude: '8.93', elevation: '891' },
      { id: 2, latitude: '46.68', longitude: '8.77', elevation: '1407' },
      { id: 3, latitude: '46.56', longitude: '8.35', elevation: '1797' },
      { id: 4, latitude: '46.73', longitude: '8.38', elevation: '1426' },
      { id: 5, latitude: '46.86', longitude: '8.65', elevation: '468' },
      { id: 6, latitude: '46.99', longitude: '9.07', elevation: '524' },
    ],
  },
  {
    id: 5,
    waypoints: [
      { id: 1, latitude: '46.99', longitude: '9.07', elevation: '524' },
      { id: 2, latitude: '47.01', longitude: '8.73', elevation: '1399' },
      { id: 3, latitude: '47.33', longitude: '8.92', elevation: '731' },
      { id: 4, latitude: '47.69', longitude: '9.27', elevation: '445' },
      { id: 5, latitude: '47.96', longitude: '9.76', elevation: '600' },
      { id: 6, latitude: '48.23', longitude: '9.87', elevation: '500' },
    ],
  },
  {
    id: 6,
    waypoints: [
      { id: 1, latitude: '48.23', longitude: '9.87', elevation: '500' },
      { id: 2, latitude: '49.28', longitude: '10.22', elevation: '441' },
      { id: 3, latitude: '50.03', longitude: '10.07', elevation: '321' },
      { id: 4, latitude: '50.93', longitude: '9.77', elevation: '210' },
      { id: 5, latitude: '51.53', longitude: '9.88', elevation: '153' },
      { id: 6, latitude: '52.26', longitude: '9.75', elevation: '68' },
    ],
  }
]);
const getDate = (departure) => {
  return new Date(Date.parse(departure)).toLocaleString('de-DE', {
    weekday: 'long',
    year: 'numeric',
    month: 'long',
    day: '2-digit'
  });
}
</script>

<template>
  <div class="weather">
    <div
      v-for="departure in departures"
      :key="departure">
      <p>
        <b>Abreise {{ getDate(departure) }}</b>
      </p>
      <div class="departure">
        <div class="temperature">
          40°<br>
          30°<br>
          20°<br>
          10°<br>
          0°
        </div>
        <div
          v-for="day in days"
          :key="day.id"
          class="day">
          <Day
            :start="departure"
            :day="day" />
        </div>
        <div class="rain">
          8 l/m²<br>
          6 l/m²<br>
          4 l/m²<br>
          2 l/m²<br>
          0 l/m²
        </div>
      </div>
    </div>
  </div>
  <div class="hours">
    <div>
      <div>08:00</div>
      <div>10:00</div>
      <div>12:00</div>
      <div>14:00</div>
      <div>16:00</div>
      <div>18:00</div>
    </div>
    <div>
      <div>08:00</div>
      <div>10:00</div>
      <div>12:00</div>
      <div>14:00</div>
      <div>16:00</div>
      <div>18:00</div>
    </div>
    <div>
      <div>08:00</div>
      <div>10:00</div>
      <div>12:00</div>
      <div>14:00</div>
      <div>16:00</div>
      <div>18:00</div>
    </div>
    <div>
      <div>08:00</div>
      <div>10:00</div>
      <div>12:00</div>
      <div>14:00</div>
      <div>16:00</div>
      <div>18:00</div>
    </div>
    <div>
      <div>08:00</div>
      <div>10:00</div>
      <div>12:00</div>
      <div>14:00</div>
      <div>16:00</div>
      <div>18:00</div>
    </div>
    <div>
      <div>08:00</div>
      <div>10:00</div>
      <div>12:00</div>
      <div>14:00</div>
      <div>16:00</div>
      <div>18:00</div>
    </div>
  </div>
</template>

<style lang="scss">
.weather {
  padding: 1rem 1rem .25rem 1rem;
  > p {
    padding-bottom: .25rem;
  }
  > svg {
    margin-right: .25rem;
  }
}
.departure {
  display: flex;
  flex-direction: row;
  margin-bottom: .5rem;
}
.day {
  padding-top: 10px;
  padding-right: 8px;
}
.temperature {
  padding-top: 0px;
  padding-right: 8px;
  line-height: 20px;
}
.rain {
  padding-top: 0px;
  padding-left: 8px;
  line-height: 20px;
}
.hours {
  padding: 0.5rem 0 0 44px;
  display: flex;
  > div {
    padding: 0 9px 0 0;
    display: flex;
    > div {
      width: 40px;
      height: 16px;
    }
  }
}
</style>
