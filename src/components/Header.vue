
<template>
  <header id='app-header'  v-if="typeof info != 'undefined'">
      
     <icon v-bind:name='weatherIcons(info.current.weather[0].main)' class="current-icon"></icon>
    
   
      <div class="current-info">
     <h1>{{cityName}}</h1>
      <p class="current-temp">{{convertToCelsius(info.current.temp)}}&degC</p>
      <p class="current-humidity">Humidity: {{info.current.humidity}}%</p>
      <p class="current-uvi">UVI: {{info.current.uvi}}%</p>
      <p class="current-wind">Wind: {{windDirection(info.current.wind_deg)}} {{convertWindSpeed(info.current.wind_speed)}}kmh</p>
      </div>
  </header>
</template>

<script>
import Icon from "./icons.vue"

export default {
  components:{
      'icon': Icon,
   },
  props:{
info:{type : Object,
required: true}
  },
  data () {
 return{
   cityName: "Barcelona, Spain",
   
 }
},
methods:
{
  convertToCelsius(kelvin){
  return (kelvin - 273.15).toFixed(0);
},
    weatherIcons(weatherStatus) {
  switch (weatherStatus) {
    case "Clouds":
      return "cloud";
      break;
    case "Clear":
      return "clear";
      break;
    case "Tornado":
    case "Sqaull":
    case "Ash":
    case "Dust":
    case "Sand":
    case "Fog":
    case "Haze":
    case "Smoke":
    case "Mist":
      return "tornado";
      break;
    case "Snow":
      return "snow";
      break;
    case "Rain":
      return "rain";
      break;
    case "Drizzle":
      return "Drizzle";
    case "Thunderstorm":
      return "thunderstrom";
  }
},
convertWindSpeed(meterSecond){
  return (meterSecond * 3.6).toFixed(0);
},
windDirection(windDegree){
  if (0 < windDegree && windDegree < 11.5) {
    return "N";
  } else if (11.5 < windDegree && windDegree <= 33.75) {
    return "N/NE";
  } else if (33.75 < windDegree && windDegree <= 56.25) {
    return "NE";
  } else if (56.25 < windDegree && windDegree <= 78.75) {
    return "E/NE";
  } else if (78.75 < windDegree && windDegree <= 101.25) {
    return "E";
  } else if (101.25 < windDegree && windDegree <= 123.75) {
    return "E/SE";
  } else if (123.75 < windDegree && windDegree <= 146.25) {
    return "SE";
  } else if (146.25 < windDegree && windDegree <= 168.75) {
    return "S/SE";
  } else if (168.75 < windDegree && windDegree <= 191.25) {
    return "S";
  } else if (191.25 < windDegree && windDegree <= 213.75) {
    return "S/SW";
  } else if (213.75 < windDegree && windDegree <= 236.25) {
    return "SW";
  } else if (236.25 < windDegree && windDegree <= 258.75) {
    return "W/SW";
  } else if (258.75 < windDegree && windDegree <= 281.25) {
    return "W";
  } else if (281.25 < windDegree && windDegree <= 303.75) {
    return "W/NW";
  } else if (303.75 < windDegree && windDegree <= 326.25) {
    return "NW";
  } else if (326.25 < windDegree && windDegree <= 348.75) {
    return "N/NW";
  } else if (348.75 < windDegree && windDegree <= 360) {
    return "N";
  }
},
}
}
</script>

<style lang="scss" scoped>
#app-header {
  display: flex;

  justify-content: space-between;
  margin: 10% auto;
}
.current-info {
  width: 60%;
}

.current-icon{
  width: 25%;
  margin: auto;
}

</style>
