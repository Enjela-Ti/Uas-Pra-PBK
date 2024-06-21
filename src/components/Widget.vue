<template>
  <div class="q-pa-md">
    <q-card>
      <q-card-section>
        <h3 class="Texth3">Widget</h3> 
        <q-input v-model="location" placeholder="Masukan Kota" />
        <q-btn @click="fetchWeather" label="Search" color="primary" class="q-ml-sm" />
      </q-card-section>

      <q-card-section v-if="weather">
        <div>{{ weather.name }}, {{ weather.sys.country }}</div>
        <div>{{ new Date(weather.dt * 1000).toLocaleTimeString() }}</div>
        <div>Temperature: {{ (weather.main.temp - 273.15).toFixed(2) }}°C</div>
        <div>Condition: {{ weather.weather[0].description }}</div>
      </q-card-section>
    </q-card>
  </div>
</template>

<script setup>
import { ref } from 'vue'
import { useQuasar } from 'quasar'

const $q = useQuasar()
const location = ref('')
const weather = ref(null)

const fetchWeather = async () => {
  const apiKey = '73b5a069a8f555ab412946fda4dba01f'
  try {
    const response = await fetch(`https://api.openweathermap.org/data/2.5/weather?q=${location.value}&appid=${apiKey}`)
    if (!response.ok) {
      throw new Error('City not found')
    }
    weather.value = await response.json()
  } catch (error) {
    $q.notify({
      type: 'negative',
      message: error.message
    })
  }
}
</script>

<style scoped>
.q-card{
  margin-top: 60px;
  background-color: rgba(237, 237, 218, 0.5);
}
.q-pa-md {
  max-width: 400px;
  margin: auto;
}
.q-ml-sm{
  margin-top: 10px;
}
.Texth3{
  text-align: center;
  margin-top: 30px;
  font-weight: bold;
  color: rgb(45, 65, 74);

}
</style>
