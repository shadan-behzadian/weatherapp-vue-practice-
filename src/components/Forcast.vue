<template>
  <!-- shows forcast weather for specific number of days -->
  <section class="forcast">
    <div class="eachDay" v-for="day in forcastInfos" :key="day[0].dayNum">
      <p class="week-name">{{ day[0].dayNum }}</p>
      <icon
        v-bind:weatherStatus="weatherIcons(day[0].weatherIcon)"
        class="weather-icon"
      ></icon>
      <p class="max-temp">{{ convertToCelsius(day[0].maxTemp) }}&degC</p>
      <p class="min-temp">{{ convertToCelsius(day[0].minTemp) }}&degC</p>
    </div>
  </section>
</template>
<script>
import Icon from "./icons.vue";
export default {
  components: {
    icon: Icon
  },
  //props recived from App.vue includes daily weather forcast data
  props: {
    dailyForcast: { type: Array, required: true }
  },
  data() {
    return {
      forcastInfos: this.forcast(this.dailyForcast)
    };
  },
  methods: {
    //recieved dynamic daily forcast data and for specific numebr of days, outputs weekday's name , max temp, min temp and weather icon for each day
    forcast(weekdays) {
      let numOfDays = 6;
      let comingDays = [];
      for (var i = 0; i < numOfDays; i++) {
        comingDays.push(weekdays[i]);
      }
      let weekday = [
        "Sunday",
        "Monday",
        "Tuesday",
        "Wednesday",
        "Thursday",
        "Friday",
        "Saturday"
      ];
      let today = new Date().getDay();
      weekday[today] = "Today";

      let displayForcast = comingDays.map(day => {
        let dayNum = new Date(day.dt * 1000).getDay();
        let maxTemp = day.temp.max;
        let minTemp = day.temp.min;
        let weatherIcon = day.weather[0].main;
        let dailyWeatherInfo = [];
        var obj = {};
        obj.dayNum = weekday[dayNum];
        obj.maxTemp = maxTemp;
        obj.minTemp = minTemp;
        obj.weatherIcon = weatherIcon;
        dailyWeatherInfo.push(obj);
        return dailyWeatherInfo;
      });

      return displayForcast;
    },
    // convert kelvin to celsius
    convertToCelsius(kelvin) {
      return (kelvin - 273.15).toFixed(0);
    },
    //recieves weather description from dynamic data and returns weather status in order to get corresponding svg icon from Icon component
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
    }
  }
};
</script>

<style lang="scss" scoped>
.eachDay {
  display: flex;
  justify-content: space-around;
  margin-top: 10px;
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
