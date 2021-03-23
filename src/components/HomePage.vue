<template>
  <div class="container-fluid m-0 p-0">
    <div id="home-page" class="full-height">        
        <div id = "main" :class = "isDay ? 'day' : 'night'">
            <div class = "container my-4 ">
                <h1 class = "title text-center"> Weather in</h1>
                <form class = "search-location" v-on:submit.prevent="getWeather">
                    <input
                    type = "text"
                    class = "form-control text-muted form-rounded p-4 shadow-sm"
                    placeholder = "What City"
                    v-model = "citySearch"
                    autocomplete = "off"
                    />
                </form>

                <p class = "text-center my-3" v-if = "cityFound">No city found</p>
                <div class = "card form-rounded my-3 shadow-lg back-card overflow-hidden" v-if = "visible">
                    <!-- weather animation container -->
                    <div>
                    <div icon = "sunny" v-if = "clearsky">
                        <span class = "sun"></span>
                    </div>

                    <div icon = "snowy" v-if = "snowy">
                        <ul>
                        <li></li>
                        <li></li>
                        <li></li>
                        <li></li>
                        <li></li>
                        <li></li>
                        <li></li>
                        <li></li>
                        <li></li>
                        <li></li>
                        <li></li>
                        <li></li>
                        <li></li>
                        </ul>
                    </div>

                    <div icon = "stormy" v-if = "stormy">
                        <span class = "cloud"></span>
                        <ul>
                            <li></li>
                            <li></li>
                            <li></li>
                            <li></li>
                            <li></li>
                        </ul>
                    </div>

                    <div icon = "cloudy" v-if = "cloudy">
                        <span class = "cloud"></span>
                        <span class = "cloud"></span>
                    </div>

                    <div icon = "nightmoon" v-if = "clearNight">
                        <span class = "moon"></span>
                        <span class = "meteor"></span>
                    </div>
                    </div>

                    <!-- Top of card starts here -->
                    <div class = "card-top text-center" style = "margin-bottom: 15rem">
                    <div class = "city-name my-3">
                        <p>{{ weather.cityName }}</p>
                        <p>{{ dateBuilder() }}</p>
                        <span>...</span>
                        <p class = "">{{ weather.country }}</p>
                    </div>
                    </div>

                    <!-- Top of card ends here -->

                    <!-- Card middle body, card body used cause i want just to update the inner -->
                    <div class = "card-body">
                    <!-- card middle starts here -->
                    <div class = "card-mid">
                        <div class = "row">
                        <div class = "col-12 text-center temp">
                            <span>{{ weather.temperature }}&deg;C</span>
                            <p class = "my-4">{{ weather.description }}</p>
                        </div>
                        </div>

                        <div class = "row">
                        <div class = "col d-flex justify-content-between px-5 mx-5">
                            <p>
                            <img src = "img/down.svg" alt = "" />
                            {{ weather.lowTemp }}&deg;C
                            </p>
                            <p>
                            <img src="img/up.svg" alt = "" />
                            {{ weather.highTemp }}&deg;C
                            </p>
                        </div>
                        </div>
                    </div>

                    <!-- card middle ends here -->

                    <!-- card bottom starts here -->
                    <div class = "card-bottom px-5 py-4 row">
                        <div class = "col text-center">
                        <p>{{ weather.feelLike }}&deg;C</p>
                        <span>Feels like</span>
                        </div>
                        <div class = "col text-center">
                        <p>{{ weather.humidity }}%</p>
                        <span>Humidity</span>
                        </div>
                    </div>

                    <!-- card bottom ends here -->
                    </div>
                </div>
            </div>
        </div>
    </div>                
</div>
</template>

<script>
export default {
    data () {
    return {
      count: 0,
      visible: false,
      cityFound: false,
      stormy: false,
      cloudy: false,
      clearsky: false,
      clearnight: false,
      snowy: false,

      isDay: true,
      citySearch: '',
      weather: {
        cityName: '',
        country: '',
        temperature: null,
        description: '',
        lowTemp: '',
        highTemp: '',
        feelLike: '',
        humidity: '',
        time: null
      }
    }
  },

  methods: {
    getWeather: async function () {
      console.log(this.citySearch)
      const key = '93a1ac5b7761599aaaeb1fd3c9ac4930'
      const baseURL = `http://api.openweathermap.org/data/2.5/weather?q=${this.citySearch}&appid=${key}&units=metric`

      // fetch weather
      try {
        const response = await fetch(baseURL)
        const data = await response.json()
        console.log(data)
        this.citySearch = ''
        this.weather.cityName = data.name
        this.weather.country = data.sys.country
        this.weather.temperature = Math.round(data.main.temp)
        this.weather.description = data.weather[0].description
        this.weather.lowTemp = Math.round(data.main.temp_min)
        this.weather.highTemp = Math.round(data.main.temp_max)
        this.weather.feelLike = Math.round(data.main.feels_like)
        this.weather.humidity = Math.round(data.main.humidity)

        const timeOfDay = data.weather[0].icon

        /// Check for time of day
        if (timeOfDay.includes('n')) {
          this.isDay = false
        } else {
          this.isDay = true
        }

        const mainweather = data.weather[0].main
        // Check weather animations
        if (mainweather.includes('Clouds')) {
          this.stormy = false
          this.cloudy = true
          this.clearSky = false
          this.clearNight = false
          this.snowy = false
        }

        if (mainweather.includes('Thunderstorm')) {
          this.stormy = true
          this.cloudy = false
          this.clearSky = false
          this.clearNight = false
          this.snowy = false
        }

        if (mainweather.includes('Clear') && this.isDay) {
          this.stormy = false
          this.cloudy = false
          this.clearSky = true
          this.clearNight = false
          this.snowy = false
        }

        if (mainweather.includes('Clouds') && !this.isDay) {
          this.stormy = false
          this.cloudy = false
          this.clearSky = false
          this.clearNight = true
          this.snowy = false
        }

        if (mainweather.includes('Snow')) {
          this.stormy = false
          this.cloudy = false
          this.clearSky = false
          this.clearNight = false
          this.snowy = true
        }

        this.visible = true
        this.cityFound = false
      } catch (error) {
        console.log(error)
        this.cityFound = true
      }
    },

    dateBuilder () {
      const d = new Date()
      const months = ['January', 'February', 'March', 'April', 'May', 'June', 'July',
        'August', 'September', 'October', 'November', 'December']
      const days = ['Sunday', 'Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday', 'Saturday']

      const day = days[d.getDay()]
      const date = d.getDate()
      const month = months[d.getMonth()]
      const year = d.getFullYear()

      return `${day} ${date} ${month} ${year}`
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoppe>
    @import "../assets/styles/animation.css";
    @import "../assets/styles/custom.css";
    
    #home-page {
        background-color: #92D2F2;
        background: url('../assets/bg_mt.jpg') no-repeat center center;
        -webkit-background-size: cover;
        -moz-background-size: cover;
        -o-background-size: cover;
        background-size: cover;
        text-align: center;
        color: #2c3e50;
    }

    #iphone-img {
        max-height: 80vh;
    }

    .app_store_img {
        max-height: 80px;
    }
</style>
