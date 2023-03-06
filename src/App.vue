<template>
  <div id="app" :class="weather.main && weather.main.temp > 16 ? 'warm' : ''">
    <main class="container">
      <search :onSubmit="fetchWeather" />
      <forecast v-if="!error" :weather="weather" />
      <modal v-if="error" :error="error" />
    </main>
  </div>
</template>

<script>
import "../src/static/css/style.css";
import axios from "axios";
import Search from "./components/Search.vue";
import Forecast from "./components/Forecast.vue";
import Modal from "./components/Modal.vue";

export default {
  name: "App",
  components: {
    Search,
    Forecast,
    Modal,
  },
  data() {
    return {
      api_key: "050eb7e35326b733e2f8c3cc210a8c99",
      url_base: "https://api.openweathermap.org/data/2.5/",
      weather: {},
      error: false,
    };
  },
  methods: {
    async fetchWeather(e, location) {
      try {
        if (e.key === "Enter") {
          const result = await axios(
            `${this.url_base}weather?q=${location}&units=metric&APPID=${this.api_key}`
          );
          const { data } = await result;

          this.setStatus({
            status: data,
            error: false,
          });
        }
      } catch (error) {
        const { response } = error;

        this.setStatus({
          status: {},
          error: response?.data?.cod,
        });
      }
    },
    setStatus({ status, error }) {
      this.weather = status;
      this.error = error;
    },
  },
};
</script>
