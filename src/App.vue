<template>
  <div>
    <div id="app" v-if="info != null">
      <main>
        <app-header v-bind:info="info"></app-header>
        <forcast v-bind:dailyForcast="info.daily"></forcast>
      </main>
    </div>
    <div v-else class="data-loading">
      <p>Loading Weather app Data...</p>
    </div>
  </div>
</template>
<script>
import Header from "./components/Header.vue";
import Forcast from "./components/Forcast.vue";
export default {
  components: {
    "app-header": Header,
    forcast: Forcast
  },
  data() {
    return {
      info: null
    };
  },
  mounted() {
    fetch(
      "https://api.openweathermap.org/data/2.5/onecall?lon=2.159&lat=41.3888&uniots=metric&appid=ad86ce3ee764480409cf4761eedd5260"
    )
      .then(res => res.json())
      .then(data => {
        this.info = data;
      })
      .catch(err => console.log(err));
  }
};
</script>
<style lang="scss">
@import url("https://fonts.googleapis.com/css2?family=Open+Sans:wght@300&display=swap");
* {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}
.forcast {
  display: flex;
}
.eachDay {
  display: flex;
  flex-direction: column;
}
#app {
  background-color: white;
  height: 100%;
  font-family: "Open Sans", sans-serif;
}
main {
  background: linear-gradient(
    rgb(128, 202, 226),
    rgb(68, 68, 223),
    rgb(24, 24, 179)
  );
  color: white;

  max-width: 900px;
  width: 100%;
  margin: 2% auto;
  font-size: 2rem;
  height: 100%;
  border-radius: 20px;
  padding: 2%;
}
.weather-icon {
  width: 30%;
}
//mediaquary-------------------------------------------------
/* Portrait  Ipad*/
@media only screen and (min-device-width: 768px) and (max-device-width: 1024px) and (orientation: portrait) and (-webkit-min-device-pixel-ratio: 2) {
  main {
    height: 130vh;
  }
  .forcast {
    display: flex;
    flex-direction: column;
  }
  .eachDay {
    display: flex;
    flex-direction: row;
    justify-content: space-around;
    margin-top: 10px;
    align-items: center;
    margin-bottom: 10%;
  }
  .eachDay p {
    width: 15%;
  }
  .eachDay div {
    width: 15%;
  }
  h1 {
    font-size: 4rem;
  }
  .current-icon {
    width: 30%;
    display: flex;
  }
  .current-info {
    width: 60%;
  }
  .weather-icon {
    width: 15%;
  }
}
/* ----------- iPhone X ----------- */
/* Portrait */
@media only screen and (min-device-width: 375px) and (max-device-width: 812px) and (-webkit-min-device-pixel-ratio: 3) and (orientation: portrait) {
  main {
    height: 100vh;
  }
  .forcast {
    display: flex;
    flex-direction: column;
  }
  .eachDay {
    display: flex;
    flex-direction: row;
    justify-content: space-around;
    margin-top: 10px;
    align-items: center;
    margin-bottom: 10%;
  }
  h1 {
    font-size: 4rem;
  }
  .current-icon {
    width: 30%;
    display: flex;
  }
  .current-info {
    width: 60%;
  }
  .weather-icon {
    width: 15%;
  }
}
/* Landscape */
@media only screen and (min-device-width: 375px) and (max-device-width: 812px) and (-webkit-min-device-pixel-ratio: 3) and (orientation: landscape) {
  #app {
    height: 100%;
  }
  main {
    height: 150vh;
    font-size: 1.5rem;
  }
  #app-header {
    display: flex;
    justify-content: end;
  }
  .current-icon {
    width: 20%;
    margin-right: 5%;
  }
  .current-info {
    width: 55%;
  }
  .weather-icon {
    width: 30%;
  }
  .eachDay {
    display: flex;
    flex-direction: column;
  }
  .forcast {
    display: flex;
    justify-content: space-between;
  }
}
/* ----------- iPhone 6+, 7+ and 8+ ----------- */
/* Portrait */
@media only screen and (min-device-width: 414px) and (max-device-width: 736px) and (-webkit-min-device-pixel-ratio: 3) and (orientation: portrait) {
  main {
    height: 100vh;
  }
  .forcast {
    display: flex;
    flex-direction: column;
  }
  .eachDay {
    display: flex;
    flex-direction: row;
    justify-content: space-around;
    margin-top: 10px;
    align-items: center;
    margin-bottom: 10%;
  }
  h1 {
    font-size: 4rem;
  }
  .current-icon {
    width: 30%;
    display: flex;
  }
  .current-info {
    width: 60%;
  }
  .weather-icon {
    width: 15%;
  }
}
/* Landscape */
@media only screen and (min-device-width: 414px) and (max-device-width: 736px) and (-webkit-min-device-pixel-ratio: 3) and (orientation: landscape) {
  #app {
    height: 100%;
  }
  main {
    font-size: 2rem;
    height: 130vh;
  }
  #app-header {
    display: flex;
    justify-content: end;
  }
  .current-icon {
    width: 20%;
    margin-right: 5%;
  }
  .current-info {
    width: 55%;
  }
  .weather-icon {
    width: 30%;
  }
  .eachDay {
    display: flex;
    flex-direction: column;
  }
  .forcast {
    display: flex;
    justify-content: space-between;
  }
}
/* ----------- iPhone 6, 6S, 7 and 8 ----------- */
/* Portrait */
@media only screen and (min-device-width: 375px) and (max-device-width: 667px) and (-webkit-min-device-pixel-ratio: 2) and (orientation: portrait) {
  main {
    height: 100vh;
  }
  .forcast {
    display: flex;
    flex-direction: column;
  }
  .eachDay {
    display: flex;
    flex-direction: row;
    justify-content: space-around;
    margin-top: 10px;
    align-items: center;
    margin-bottom: 10%;
  }
  h1 {
    font-size: 4rem;
  }
  .current-icon {
    width: 30%;
    display: flex;
  }
  .current-info {
    width: 60%;
  }
  .weather-icon {
    width: 15%;
  }
}
/* Landscape */
@media only screen and (min-device-width: 375px) and (max-device-width: 667px) and (-webkit-min-device-pixel-ratio: 2) and (orientation: landscape) {
  #app {
    height: 100%;
  }
  main {
    font-size: 2rem;
  }
  #app-header {
    display: flex;
    justify-content: end;
  }
  .current-icon {
    width: 20%;
    margin-right: 5%;
  }
  .current-info {
    width: 55%;
  }
  .weather-icon {
    width: 30%;
  }
  .eachDay {
    display: flex;
    flex-direction: column;
  }
  .forcast {
    display: flex;
    justify-content: space-between;
  }
}

/* ----------- iPhone 5, 5S, 5C and 5SE ----------- */
/* Portrait */
@media only screen and (min-device-width: 320px) and (max-device-width: 568px) and (-webkit-min-device-pixel-ratio: 2) and (orientation: portrait) {
  main {
    height: 100vh;
  }
  .forcast {
    display: flex;
    flex-direction: column;
  }
  .eachDay {
    display: flex;
    flex-direction: row;
    justify-content: space-around;
    align-items: center;
    margin-bottom: 10%;
  }
  .eachDay p {
    width: 15%;
  }
  .eachDay div {
    width: 15%;
  }
  h1 {
    font-size: 4rem;
  }
  .current-icon {
    width: 30%;
    display: flex;
  }
  .current-info {
    width: 60%;
  }
  .weather-icon {
    width: 15%;
  }
}
/* Landscape */
@media only screen and (min-device-width: 320px) and (max-device-width: 568px) and (-webkit-min-device-pixel-ratio: 2) and (orientation: landscape) {
  #app {
    height: 100%;
  }
  main {
    font-size: 2rem;
  }
  #app-header {
    display: flex;
    justify-content: end;
  }
  .current-icon {
    width: 20%;
    margin-right: 5%;
  }
  .current-info {
    width: 40%;
  }
  .weather-icon {
    width: 30%;
  }
  .eachDay {
    display: flex;
    flex-direction: column;
  }
  .forcast {
    display: flex;
    justify-content: space-between;
  }
}
/* ----------- iPhone 4 and 4S ----------- */
/* Portrait */
@media only screen and (min-device-width: 320px) and (max-device-width: 480px) and (-webkit-min-device-pixel-ratio: 2) and (orientation: portrait) {
  main {
    height: 120vh;
  }
  .forcast {
    display: flex;
    flex-direction: column;
  }
  .current-icon {
    width: 30%;
    display: flex;
  }
  .current-info {
    width: 60%;
  }
  .eachDay {
    display: flex;
    flex-direction: row;
    justify-content: space-around;
    margin-top: 10px;
    align-items: center;
    margin-bottom: 10%;
  }
  h1 {
    font-size: 4rem;
  }
  .weather-icon {
    width: 15%;
  }
}
/* ----------- iPhone 4 and 4S ----------- */

/* Landscape */
@media only screen and (min-device-width: 320px) and (max-device-width: 480px) and (-webkit-min-device-pixel-ratio: 2) and (orientation: landscape) {
  #app {
    height: 100%;
  }
  main {
    font-size: 2rem;
  }
  #app-header {
    display: flex;
    justify-content: end;
  }
  .current-icon {
    width: 20%;
    margin-right: 5%;
  }
  .current-info {
    width: 40%;
  }
  .weather-icon {
    width: 20%;
  }
  .eachDay {
    display: flex;
    flex-direction: column;
    margin: auto 10px auto 10px;
  }
  .forcast {
    display: flex;
    justify-content: space-between;
  }
}
</style>
