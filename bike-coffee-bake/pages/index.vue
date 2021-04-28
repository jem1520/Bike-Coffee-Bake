<template>
  <!-- homepage html and bootstrap classes for page styling-->
  <div class="homepage">
    <div class="container text-center pt-5">
      <h1>{{welcome}}</h1>
    </div>
    <p class="lead m-5">{{filltext}}</p>
    <!-- Jumbotron on page -->
    <div class="container">
      <div class="jumbotron">
        <h2 class="h1">{{ homepageheader }}</h2>
        <h5 class="mb-4">{{homesubheader}}</h5>
        <ul>
          <li v-for="service in services" :key="service.id">
            {{service}}
          </li>
        </ul>
      </div>
    </div>
    <!-- Like our business button and likes counter -->
    <div class="container text-center">
      <p class="lead m-5">{{filltext}}</p>
      <p v-if="show" class="lead m-5">{{like}}</p>
      <p v-else class="lead m-5" >{{thanks}}</p>
      <button type="button" class="btn btn-success" v-on:click="show = !show, counter += 1">Like!</button>
      <p class="lead m-5">{{likes}}{{counter}}</p>
   </div>
   <!-- homepage animations-->
   <div>
     <img class="wheelicon" :src="bikeiconimg" :alt="bikeicon">
     <img class="chemexicon" :src="chemexiconimg" :alt="chemexicon">
     <img class="breadicon" :src="loaficonimg" :alt="loaficon">
   </div>
    <!-- Weather data from API and tooltip further description-->
   <div class="container text-center">
     <h4 data-toggle="tooltip" data-placement="top" title="Lat/Long,Humidity/Pressure,Windspeed/Direction(degrees)" class="p-4">{{localweather}}</h4>
     <div class="container" v-if="weather">
       <weather
         v-for="weatherdata of weather"
         v-bind:key="weatherdata.id"
         v-bind:weatherdata="weatherdata">
       </weather>
     </div>
     <h4 class="p-4 m-4">{{localtime}}</h4>
    </div>
  </div>
</template>


<script>
//importing axios
import axios from 'axios'

import weather from '../components/weatherAPI.vue'
//import images for animations
import bikeiconimg from "../assets/BikeWheelGraphic.svg"
import chemexiconimg from "../assets/ChemexIcon-1.svg"
import loaficonimg from "../assets/BreadIcon.svg"

// hompage content from array and variables
export default {
  name: 'homepage',
  components: {
    weather
  },
  data(){
    return {
        show: true,
        welcome: 'Welcome to Bike Coffee Bake!',
        services:['Full Bike Service', 'Craft Pourovers + Coldbrew','Fresh Pastries Daily'],
        homepageheader: "Best Coffee & Bike Shop",
        homesubheader: "Rated BEST by Winston Living 2021",
        filltext: "Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.",
        like: 'Like Our Business!',
        thanks: 'Thanks!',
        counter: 0,
        likes: 'likes ',
        bikeicon: 'bike wheel icon',
        chemexicon: 'Chemex coffee maker icon',
        loaficon: 'loaf of bread icon',
        bikeiconimg: bikeiconimg,
        chemexiconimg: chemexiconimg,
        loaficonimg: loaficonimg,
        localweather: 'Our Location & Current Atmospheric Conditions',
        localtime: 'Perfect for biking and coffee!',
        weather: null,
        loading: true,
        errored: false
      }
    },
    //calling API data
    mounted () {
      axios
        .get('https://api.openweathermap.org/data/2.5/weather?q=winston-salem&appid=6b16e973abb4af7a3de56756af96cc52')
        .then(response => (this.weather = response.data))
        .catch(error => {
          console.error(error)
          this.errored = true
        })
        .finally(() => this.loading = false)
    },
  //head content
  head () {
  return {
    title: this.title,
    meta: [
         { hid: 'description', name: 'description', content: 'Bike Coffee Bake. The Best Coffe And Bike Shop' }
         ]
      }
    }
  }

</script>


<style lang="scss">
// Rotate transitions
$rotate-bikewheel: rotate(1080deg);
$rotate-chemex: rotate(120deg);


@mixin animations {
  transition: all 3s;
  transition-timing-function: ease;
}

// Settings for icon size and position
@mixin iconsize {
  height: auto;
  width: 15rem;
  margin: 8%;
}

// Bike wheel icon rotate animation
.wheelicon {
  @include iconsize;

  &:hover {
    transform: $rotate-bikewheel;
    @include animations;
  }
}

// Chemex icon pour animation
.chemexicon {
  @include iconsize;

  &:hover {
    transform: $rotate-chemex;
    transition: all 2s;
    transition-timing-function: ease-out;
  }
}

// Bread icon double in size animation
.breadicon {
  @include iconsize;
  padding-bottom: 2%;

  &:hover {
    transform: scale(2);
    @include animations;
  }
}

.border-width {
  border-width: 5px;
}
</style>
