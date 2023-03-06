<template>
  <div class="forcast-conatiner">
    <div class="weather-wrap" v-if="weather.main">
      <div class="location-box">
        <div class="location">{{ weather.name }}, {{ weather.sys.country }}</div>
        <div class="date">{{ dateBuilder() }}</div>
      </div>
      <div class="weather-box">
        <div class="temp">{{ Math.round(weather.main.temp) }}°c</div>
        <div class="weather">{{ weather.weather[0].main }}</div>
      </div>
      <div class="weather-details">
        <div class="box">
          <div class="title">
            <img src="../static/assets/cold.png" alt="mintemp" />
            <p>Min Temp</p>
          </div>
          <h1>{{ weather.main.temp_min }}°c</h1>
        </div>
        <div class="box">
          <div class="title">
            <img src="../static/assets/hot.png" alt="maxtemp" />
            <p>Max Temp</p>
          </div>
          <h1>{{ weather.main.temp_max }}°c</h1>
        </div>

        <div class="box">
          <div class="title">
            <img src="../static/assets/celsius.png" alt="felttemp" />
            <p>Felt Temp</p>
          </div>
          <h1>{{ weather.main.feels_like }}°c</h1>
        </div>
        <div class="box">
          <div class="title">
            <img src="../static/assets/visibility.png" alt="visibility" />
            <p>Visibility</p>
          </div>
          <h1>{{ weather.visibility }}</h1>
        </div>
        <div class="box">
          <div class="title">
            <img src="../static/assets/wind.png" alt="wind" />
            <p>Wind</p>
          </div>
          <h1>{{ weather.wind.speed }} km/h</h1>
        </div>
        <div class="box">
          <div class="title">
            <img src="../static/assets/humidity.png" alt="humidity" />
            <p>Humidity</p>
          </div>

          <h1>{{ weather.main.humidity }} %</h1>
        </div>
      </div>
    </div>
    <div class="info" v-else>
      <img src="../static/assets/weather.png" alt="weather" />
      <h2>Get your local weather at a glance</h2>
    </div>
  </div>
</template>

<script>
export default {
  name: "ForcastBox",
  props: ["weather"],
  methods: {
    dateBuilder() {
      const date = new Date();
      const options = { weekday: "long", year: "numeric", month: "long", day: "numeric" };
      return date.toLocaleDateString("en-US", options);
    },
  },
};
</script>
