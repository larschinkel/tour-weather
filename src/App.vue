<script setup>
import { ref } from 'vue'
import Day from './components/Day.vue'
const departures = ref([
  ['2025-08-19','2025-08-20', '2025-08-21', '2025-08-22', '2025-08-23', '2025-08-24', '2025-08-25'],
  // ['2025-08-20', '2025-08-21', '2025-08-22', '2025-08-23', '2025-08-24', '2025-08-25', '2025-08-26'],
  // ['2025-08-21', '2025-08-22', '2025-08-23', '2025-08-24', '2025-08-25', '2025-08-26', '2025-08-27'],
  // ['2025-08-22', '2025-08-23', '2025-08-24', '2025-08-25', '2025-08-26', '2025-08-27', '2025-08-28'],
  ['2025-08-27','2025-08-28', '2025-08-29', '2025-08-30', '2025-08-31', '2025-09-01', '2025-09-02'],
  // ['2025-08-28', '2025-08-29', '2025-08-30', '2025-08-31', '2025-09-01', '2025-09-02', '2025-09-03'],
  // ['2025-08-29', '2025-08-30', '2025-08-31', '2025-09-01', '2025-09-02', '2025-09-03', '2025-09-04'],
]);
const days = ref([
  [
    { id: 1, latitude: '52.267803', longitude: '9.7598370' },
    { id: 2, latitude: '51.451977', longitude: '9.8674120' },
    { id: 3, latitude: '50.666714', longitude: '9.7619430' },
    { id: 4, latitude: '49.882139', longitude: '9.9956470' },
    { id: 5, latitude: '49.039406', longitude: '10.184144' },
    { id: 6, latitude: '48.231863', longitude: '9.8833610' },
  ],
  [
    { id: 1, latitude: '48.231863', longitude: '9.8833610' },
    { id: 2, latitude: '47.799852', longitude: '9.6077970' },
    { id: 3, latitude: '47.422045', longitude: '9.3558220' },
    { id: 4, latitude: '47.203489', longitude: '9.3503010' },
    { id: 5, latitude: '46.923628', longitude: '9.7284910' },
    { id: 6, latitude: '46.698325', longitude: '10.096986' },
  ],
  [
    { id: 1, latitude: '46.698325', longitude: '10.096986' },
    { id: 2, latitude: '46.544694', longitude: '10.434780' },
    { id: 3, latitude: '46.536500', longitude: '10.155520' },
    { id: 4, latitude: '46.542377', longitude: '9.8875130' },
    { id: 5, latitude: '46.649113', longitude: '9.5792890' },
    { id: 6, latitude: '46.434050', longitude: '9.7517600' },
  ],
  [
    { id: 1, latitude: '46.434050', longitude: '9.7517600' },
    { id: 2, latitude: '46.371912', longitude: '9.3594520' },
    { id: 3, latitude: '46.517528', longitude: '9.1849280' },
    { id: 4, latitude: '46.231357', longitude: '9.1095380' },
    { id: 5, latitude: '46.524169', longitude: '8.9302510' },
    { id: 6, latitude: '46.679060', longitude: '8.7685700' },
  ],
  [
    { id: 1, latitude: '46.679060', longitude: '8.7685700' },
    { id: 2, latitude: '46.571857', longitude: '8.4096260' },
    { id: 3, latitude: '46.711013', longitude: '8.2487130' },
    { id: 4, latitude: '46.707968', longitude: '8.5982750' },
    { id: 5, latitude: '46.871150', longitude: '8.8166200' },
    { id: 6, latitude: '47.024344', longitude: '9.0800900' },
  ],
  [
    { id: 1, latitude: '47.024344', longitude: '9.0800900' },
    { id: 2, latitude: '47.006522', longitude: '8.7226800' },
    { id: 3, latitude: '47.266811', longitude: '8.9191740' },
    { id: 4, latitude: '47.656743', longitude: '9.1245520' },
    { id: 5, latitude: '47.862701', longitude: '9.6640730' },
    { id: 6, latitude: '48.231863', longitude: '9.8833610' },
  ],
  [
    { id: 1, latitude: '48.231863', longitude: '9.8833610' },
    { id: 2, latitude: '49.039406', longitude: '10.184144' },
    { id: 3, latitude: '49.882139', longitude: '9.9956470' },
    { id: 4, latitude: '50.666714', longitude: '9.7619430' },
    { id: 5, latitude: '51.451977', longitude: '9.8674120' },
    { id: 6, latitude: '52.267803', longitude: '9.7598370' },
  ],
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
      v-for="(departure, departure_key) in departures"
      :key="departure_key">
      <p>
        <b>Abreise {{ getDate(departure[0]) }}</b>
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
          v-for="(day, day_key) in days"
          :key="day_key"
          class="day">
          <Day
            :start="departure[day_key]"
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
  padding-top: 19px;
  padding-right: 8px;
  line-height: 20px;
}
.rain {
  padding-top: 19px;
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
