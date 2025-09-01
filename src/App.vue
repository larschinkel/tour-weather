<script setup>
import { ref } from 'vue'
import Day from './components/Day.vue'
const departures = ref([
  ['2025-09-02', '2025-09-03', '2025-09-04', '2025-09-05', '2025-09-06', '2025-09-07', '2025-09-08'],
  ['2025-09-03', '2025-09-04', '2025-09-05', '2025-09-06', '2025-09-07', '2025-09-08', '2025-09-09'],
  ['2025-09-04', '2025-09-05', '2025-09-06', '2025-09-07', '2025-09-08', '2025-09-09', '2025-09-10'],
  ['2025-09-05', '2025-09-06', '2025-09-07', '2025-09-08', '2025-09-09', '2025-09-10', '2025-09-11'],
  ['2025-09-06', '2025-09-07', '2025-09-08', '2025-09-09', '2025-09-10', '2025-09-11', '2025-09-12'],
]);
const days = ref([
  // Mittelgebirge
  // [
  //   { id: 1, latitude: '52.264552', longitude: '9.6284810' },
  //   { id: 2, latitude: '52.264552', longitude: '9.6284810' },
  //   { id: 3, latitude: '51.658368', longitude: '8.7664660' },
  //   { id: 4, latitude: '51.465028', longitude: '8.2387130' },
  //   { id: 5, latitude: '51.211932', longitude: '8.0078230' },
  //   { id: 6, latitude: '50.931942', longitude: '7.5658250' },
  // ],
  // [
  //   { id: 1, latitude: '50.931942', longitude: '7.5658250' },
  //   { id: 2, latitude: '50.706114', longitude: '7.0210270' },
  //   { id: 3, latitude: '50.561380', longitude: '6.5357400' },
  //   { id: 4, latitude: '50.462177', longitude: '6.5524020' },
  //   { id: 5, latitude: '50.376729', longitude: '6.9510050' },
  //   { id: 6, latitude: '50.169532', longitude: '7.2992990' },
  // ],
  // [
  //   { id: 1, latitude: '50.169532', longitude: '7.2992990' },
  //   { id: 2, latitude: '49.834946', longitude: '7.5725930' },
  //   { id: 3, latitude: '49.435437', longitude: '7.7535890' },
  //   { id: 4, latitude: '49.086400', longitude: '7.6822200' },
  //   { id: 5, latitude: '48.695932', longitude: '7.7838880' },
  //   { id: 6, latitude: '48.711806', longitude: '8.2376860' },
  // ],
  // [
  //   { id: 1, latitude: '48.711806', longitude: '8.2376860' },
  //   { id: 2, latitude: '48.496578', longitude: '8.1875370' },
  //   { id: 3, latitude: '48.156964', longitude: '8.1592830' },
  //   { id: 4, latitude: '47.956428', longitude: '7.9510730' },
  //   { id: 5, latitude: '47.764546', longitude: '8.1227340' },
  //   { id: 6, latitude: '47.883255', longitude: '8.7264920' },
  // ],
  // [
  //   { id: 1, latitude: '47.883255', longitude: '8.7264920' },
  //   { id: 2, latitude: '48.076900', longitude: '9.1630500' },
  //   { id: 3, latitude: '48.401843', longitude: '9.5092670' },
  //   { id: 4, latitude: '48.554851', longitude: '10.1335670' },
  //   { id: 5, latitude: '48.774602', longitude: '10.6443930' },
  //   { id: 6, latitude: '48.892205', longitude: '11.1801340' },
  // ],
  // [
  //   { id: 1, latitude: '48.892205', longitude: '11.1801340' },
  //   { id: 2, latitude: '49.088932', longitude: '11.7968660' },
  //   { id: 3, latitude: '49.481762', longitude: '11.4759620' },
  //   { id: 4, latitude: '49.879271', longitude: '11.2447470' },
  //   { id: 5, latitude: '50.089493', longitude: '10.7879240' },
  //   { id: 6, latitude: '50.349739', longitude: '10.2542410' },
  // ],
  // [
  //   { id: 1, latitude: '50.349739', longitude: '10.2542410' },
  //   { id: 2, latitude: '50.692466', longitude: '9.9607370' },
  //   { id: 3, latitude: '51.104847', longitude: '9.9668200' },
  //   { id: 4, latitude: '51.483825', longitude: '9.7796220' },
  //   { id: 5, latitude: '51.883563', longitude: '9.6833820' },
  //   { id: 6, latitude: '52.264552', longitude: '9.6284810' },
  // ]
  // Schweiz
  [
    { id: 1, latitude: '52.267803', longitude: '9.7598370', elevation: 68 },
    { id: 2, latitude: '51.451977', longitude: '9.8674120', elevation: 205 },
    { id: 3, latitude: '50.666714', longitude: '9.7619430', elevation: 262 },
    { id: 4, latitude: '49.882139', longitude: '9.9956470', elevation: 329 },
    { id: 5, latitude: '49.039406', longitude: '10.184144', elevation: 510 },
    { id: 6, latitude: '48.231863', longitude: '9.8833610', elevation: 513 },
  ],
  [
    { id: 1, latitude: '48.231863', longitude: '9.8833610', elevation: 513 },
    { id: 2, latitude: '47.799852', longitude: '9.6077970', elevation: 434 },
    { id: 3, latitude: '47.422045', longitude: '9.3558220', elevation: 680 },
    { id: 4, latitude: '47.203489', longitude: '9.3503010', elevation: 1095 },
    { id: 5, latitude: '46.923628', longitude: '9.7284910', elevation: 739 },
    { id: 6, latitude: '46.698325', longitude: '10.096986', elevation: 1470 },
  ],
  [
    { id: 1, latitude: '46.698325', longitude: '10.096986', elevation: 1470 },
    { id: 2, latitude: '46.544694', longitude: '10.434780', elevation: 2490 },
    { id: 3, latitude: '46.536500', longitude: '10.155520', elevation: 2157 },
    { id: 4, latitude: '46.542377', longitude: '9.8875130', elevation: 1702 },
    { id: 5, latitude: '46.649113', longitude: '9.5792890', elevation: 1045 },
    { id: 6, latitude: '46.434050', longitude: '9.7517600', elevation: 1814 },
  ],
  [
    { id: 1, latitude: '46.434050', longitude: '9.7517600', elevation: 1814 },
    { id: 2, latitude: '46.371912', longitude: '9.3594520', elevation: 928 },
    { id: 3, latitude: '46.517528', longitude: '9.1849280', elevation: 1858 },
    { id: 4, latitude: '46.231357', longitude: '9.1095380', elevation: 282 },
    { id: 5, latitude: '46.524169', longitude: '8.9302510', elevation: 997 },
    { id: 6, latitude: '46.679060', longitude: '8.7685700', elevation: 1430 },
  ],
  [
    { id: 1, latitude: '46.679060', longitude: '8.7685700', elevation: 1430 },
    { id: 2, latitude: '46.571857', longitude: '8.4096260', elevation: 2419 },
    { id: 3, latitude: '46.711013', longitude: '8.2487130', elevation: 785 },
    { id: 4, latitude: '46.707968', longitude: '8.5982750', elevation: 935 },
    { id: 5, latitude: '46.871150', longitude: '8.8166200', elevation: 1671 },
    { id: 6, latitude: '47.024344', longitude: '9.0800900', elevation: 517 },
  ],
  [
    { id: 1, latitude: '47.024344', longitude: '9.0800900', elevation: 517 },
    { id: 2, latitude: '47.006522', longitude: '8.7226800', elevation: 1174 },
    { id: 3, latitude: '47.266811', longitude: '8.9191740', elevation: 619 },
    { id: 4, latitude: '47.656743', longitude: '9.1245520', elevation: 432 },
    { id: 5, latitude: '47.862701', longitude: '9.6640730', elevation: 511 },
    { id: 6, latitude: '48.231863', longitude: '9.8833610', elevation: 513 },
  ],
  [
    { id: 1, latitude: '48.231863', longitude: '9.8833610', elevation: 513 },
    { id: 2, latitude: '49.039406', longitude: '10.184144', elevation: 510 },
    { id: 3, latitude: '49.882139', longitude: '9.9956470', elevation: 329 },
    { id: 4, latitude: '50.666714', longitude: '9.7619430', elevation: 262 },
    { id: 5, latitude: '51.451977', longitude: '9.8674120', elevation: 205 },
    { id: 6, latitude: '52.267803', longitude: '9.7598370', elevation: 68 },
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
