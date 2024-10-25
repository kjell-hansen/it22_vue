<script setup>
import { getCurrent } from '@/services/forecastService';
import { ref, watchEffect } from 'vue';
import wc from "@/assets/data/weatherCodes.json"

const currentLocation = ref({})
const weather = ref({})
const loading = ref(true)
const props = defineProps(['location'])
const weatherCodes = ref(wc)


watchEffect(() => {
    loading.value = true
    let locationsList = JSON.parse(localStorage.getItem("locations"))

    currentLocation.value = locationsList.find(loc => {
        return loc.name.toLocaleLowerCase() === props.location.toLocaleLowerCase()
    })
    getCurrent(currentLocation.value)
        .then(response => {
            weather.value = response
            loading.value = false
        })
        .catch(err => {
            console.log(err)
        })
})

function getText(code) {
    let wcText = weatherCodes.value.find(itm => {
        return itm.code == code
    }).description ?? 'Unknown'

    return wcText
}
</script>
<template>
    <template v-if="loading">
        loading...
    </template>
    <template v-else>
        <ul>
            <li>Created: <span>{{ new Date(weather.time).getDate() }}.{{ new Date(weather.time).getMonth() + 1 }} {{
                weather.time.substr(weather.time.indexOf('T') + 1) }}</span> (Updated in {{
                        parseInt(weather.interval / 60) }}minutes)
            </li>
            <li>Weather
                <ul>
                    <li>{{ getText(weather.weather.code) }}</li>
                    <li>Overcast: {{ weather.weather.cloud.cover + weather.weather.cloud.unit }}</li>

                </ul>
            </li>
            <li>Temp
                <ul>
                    <li>{{ weather.weather.temp.temp + weather.weather.temp.unit }}</li>
                    <li>{{ weather.weather.temp.humidity + weather.weather.temp.humidity_unit }} humudity</li>
                    <li>Feels like {{ weather.weather.temp.apparent + weather.weather.temp.unit }}</li>
                </ul>
            </li>
            <li>Precip
                <ul>
                    <li>{{ weather.weather.precipitation.precipitation + weather.weather.precipitation.unit }}</li>
                </ul>
            </li>
            <li>Wind
                <ul>
                    <li>{{ Math.round(weather.weather.wind.speed) + weather.weather.wind.unit }}</li>
                    <li>{{ weather.weather.wind.direction + weather.weather.wind.direction_unit }}</li>
                    <li>Gusts {{ Math.round(weather.weather.wind.gusts) + weather.weather.wind.unit }}</li>
                </ul>
            </li>
            <li>Pressure
                <ul>
                    <li>{{ weather.weather.pressure.pressure + weather.weather.pressure.unit }}</li>
                </ul>
            </li>
        </ul>
    </template>

</template>
<style scoped></style>