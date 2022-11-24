<template>
  <div id="app" :class="typeof weather.main != 'undefined' && weather.main.temp > 16 ? 'warm' : ''">
    <main class=" bg-gradient-to-b from-indigo-900  to-green-500 h-screen">
      <div class="max-w-4xl mx-auto">
        <Header />
        <div class="flex flex-col">
          <div class="p-10">
            <input type="text"
              class="w-full rounded-lg text-gray-100 border-2 border-violet-400 p-2 bg-inherit focus:outline-none focus:border-blue-500"
              placeholder="Enter location here..." v-model="query" @keypress="fetchWeather" />
          </div>
          <div class="flex flex-col justify-center p-10 text-white" v-if="typeof weather.main != 'undefined'">
            <div class="flex flex-col justify-center text-center my-10">
              <div class="location lg:text-4xl text-2xl">{{ weather.name }}, {{ weather.sys.country }}</div>
              <div class="date lg:text-3xl text-xl">{{ dateBuilder() }}</div>
            </div>
            <div class="flex flex-col justify-center text-center my-10">
              <div class="font-bold lg:text-4xl text-2xl">{{ Math.round(weather.main.temp) }}°c</div>
              <div class="font-semibold lg:text-lg text-sm">{{ weather.weather[0].main }}</div>
            </div>
          </div>
        </div>
        <Footer/>
      </div>
    </main>
  </div>
</template>

<script>
import Header from './components/Header.vue' 
export default {
  name: 'app', 
  components: {
    Header, 
  },
  data() {
    return {
      api_key: process.env.VUE_APP_OPEN_WEATHER_API_KEY,
      url_base: process.env.VUE_APP_OPEN_WEATHER_API_URL,
      query: '',
      weather: {}
    }
  },
  methods: {
    fetchWeather(e) {
      if (e.key == "Enter") {
        fetch(`${this.url_base}weather?q=${this.query}&units=metric&APPID=${this.api_key}`)
          .then(res => {
            return res.json();
          }).then(this.setResults);
      }
    },
    setResults(results) {
      this.weather = results;
    },
    dateBuilder() {
      let d = new Date();
      let months = ["January", "February", "March", "April", "May", "June", "July", "August", "September", "October", "November", "December"];
      let days = ["Sunday", "Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday"];

      let day = days[d.getDay()];
      let date = d.getDate();
      let month = months[d.getMonth()];
      let year = d.getFullYear();

      return `${day} ${date} ${month} ${year}`;
    },
  }
}
</script>

<style>
* {
  font-family: 'Patrick Hand', cursive;
}

@import url('https://fonts.googleapis.com/css2?family=Patrick+Hand&display=swap');
</style>