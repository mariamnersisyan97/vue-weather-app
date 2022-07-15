<template>
  <div id="app">
    <main>
      <div class="search-box">
        <input type="text" class="search-bar" placeholder="Search..."
        v-model="query"
        @keypress="fetchWeather"/>{{ query }}
      </div>

      <div class="weather-wrap" v-if="typeof weather.main != 'undefined'">
        <div class="location-box">
        <div class="location">{{ weather.name}}, {{ weather.sys.country }}</div>
        </div>
          <div class="date"> Sunday 20 January 2022
            </div>
            <div class="weather-box">
              <div class="temp">9°c</div>
                <div class="weather">Rain</div>
              
              
            
          
        </div>
      </div>
    </main>
  </div>
</template>

<script>
  export default {
    name: 'app',
    data(){
      return {
        api_key,
        baseURL: 'https://api.openweathermap.org/data/2.5/',
        weather: {},
        query: '',

      }
    },
    methods: {
      fetchWeather () {
        if(e.key == "Enter"){
          fetch(`${this.baseURL}weather?q=${this.query}&units=metric&APPID=${this.api_key}`)
          .then(res => {
            return res.json();
        
          }).then(this.setResults);
        }
      },
      setResults(results){
        this.weather = results;
      }
    }
  }
</script>

<!-- CSS libraries -->
<style src="normalize.css/normalize.css"></style>

<!-- Global CSS -->
<style>
 *{
  margin: 0;
  padding: 0;
  box-sizing: border-box;

 }

 body {
  font-family: 'montserrat', sans-serif;
 }

 #app {
  background-image: url('./assets/clouds.jpg');
  background-size: cover;
  background-position: bottom;
  transition: 0.5s;
 }

 main {
  min-height: 100vh;
  padding: 25px;
  background-image: linear-gradient(to bottom, rgba(0,0,0,0.25), rgba(0,0,0,0.75));
 }
 
 .search-box {
  width: 100%;
  margin-bottom: 30px;
 }

 .search-box .search-bar {
  display: block;
  width: 100%;
  color: #313131;
  font-size: 20px;
  appearance: none;
  border: none;
  background: none;
  outline:none;
  background-color: rgba(255,255,255,0.5);
  border-radius: 0px 16px 0px 16px;
  transition: 0.5s;
  box-shadow: 0px 0px 8px rgba(0,0,0,0.25);
}

.search-box .search-bar:focus {
  box-shadow:0px 0px 18px rgba(0,0,0,0.25);
  background-color: rgba(255,255,255,0.75);
}
.location-box .location {
color: #fff;
font-size: 32px;
font-weight: 500;
text-align: center;
}
.date {
  text-align: center;
  color: beige;
  padding: 10px;
  font-style: italic;
}
.weather-box {
  text-align: center;
  color: #FFF;
}
.weather-box .temp {
  display: inline-block;
  padding: 10px 30px;
  font-size: 100px;
  font-weight: 700;
  background-color: lightcyan;
  border-radius: 30px;
  text-shadow: 3px 6px rgba(0,0,0,0.25);
  opacity: 0.6;
}
</style>
