<template>
 <section class="forcast">
      <div class="eachDay" v-for="day in weekNames" :key="day" > 
          <p class="week-name"  >{{day[0].dayNum}}</p>
<icon v-bind:name="weatherIcons(day[0].weatherIcon)" class="weather-icon"></icon>
    <p  class="max-temp" >{{convertToCelsius(day[0].maxTemp)}}&degC</p>
    <p   class="min-temp" >{{convertToCelsius(day[0].minTemp)}}&degC</p>
    
    </div>
     </section>
</template>

<script>
import Icon from "./icons.vue"
export default {
   components:{
      'icon': Icon,
   },
  props:{
dailyForcast:{type : Array,
required: true
  }
  },
  data () {
   return{
      weekNames: this.forcast(this.dailyForcast),
      // maxTemp: "",
      // minTemp: ""

   }
  },
methods:{
    forcast(weekdays){
  let comingDays = [];
  for (var i = 0; i < 6; i++) {
    comingDays.push(weekdays[i]);
  }
  let weekday = ["Sunday","Monday","Tuesday","Wednesday","Thursday","Friday","Saturday"]
  let today = new Date().getDay();
  weekday[today] = "Today";

  let displayForcast = comingDays.map((day) => {
    let dayNum = new Date(day.dt * 1000).getDay();
    let maxTemp = day.temp.max;
    let minTemp = day.temp.min;
    let weatherIcon = day.weather[0].main
    // return `${weekday[dayNum]} ${this.convertToCelsius(maxTemp)} ${this.convertToCelsius(minTemp)}`
let myArray = [];
var obj = {};
obj.dayNum = weekday[dayNum];
obj.maxTemp = maxTemp;
obj.minTemp =minTemp;
obj.weatherIcon = weatherIcon;
myArray.push(obj);
return myArray
  });
  
return  displayForcast
},
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
      return "drizzle";
    case "Thunderstorm":
      return "thunderstorm";
  }
},

}

}
</script>

<style lang="scss" >
.eachDay {
  display: flex;
  justify-content: space-around;
  margin-top: 20px;
  align-items: center;
  margin-bottom: 10%;
}
.max-temp {
  color: red;
}
.min-temp {
  color: aqua;
}

</style>
