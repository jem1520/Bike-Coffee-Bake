<template>
 <!-- setting up main app html and including bootstrap classes for page styling-->
  <div id="app">
    <!-- setting up header content -->
    <h2 class="display-1 text-center">{{ header }}</h2>
    <img :src="logoimage" class="mx-auto d-block" :alt="logoimgtext" style="width:40%;">
    <h3 class="display-4 text-center mb-3">{{ subheader }}</h3>
    <!-- Responsive navigation menu -->
    <div id="nav">
      <nav class="navbar text-uppercase navbar-expand-lg navbar-light bg-primary">
        <div class="container">
          <button class="navbar-toggler" data-toggle="collapse" data-target="#navbarNav"><span class="navbar-toggler-icon"></span></button>
          <div id="navbarNav" class="collapse navbar-collapse">
            <div class="navbar-nav">
              <nuxt-link to="/" class="nav-link nav-item ml-5">Home</nuxt-link>
              <nuxt-link to="/bikeshop" class="nav-link nav-item ml-5">Bikeshop</nuxt-link>
              <nuxt-link to="/coffeeshop" class="nav-link nav-item ml-5">Coffeeshop</nuxt-link>
              <nuxt-link to="/bakeshop" class="nav-link nav-item ml-5">Bakeshop</nuxt-link>
            </div>
          </div>
        </div>
      </nav>
      <router-view></router-view>
    </div>
    <!-- app views content shows up here -->
    <!-- Responsive footer elements with additional nav menu -->
    <img :src="footerimage" class="img-fluid" :alt="footerimgtext">
    <div id="nav">
      <nav class="navbar text-uppercase navbar-expand-sm bg-dark">
        <div class="container">
          <div class="navbar-nav">
            <nuxt-link to="/" class="nav-link nav-item ml-5">Home</nuxt-link>
            <nuxt-link to="/bikeshop" class="nav-link nav-item ml-5">Bikeshop</nuxt-link>
            <nuxt-link to="/coffeeshop" class="nav-link nav-item ml-5">Coffeeshop</nuxt-link>
            <nuxt-link to="/bakeshop" class="nav-link nav-item ml-5">Bakeshop</nuxt-link>
          </div>
        </div>
      </nav>
      <p class="text-center mt-2">{{ footertext }}</p>
    </div>
  </div>
</template>


<script>
// importing image assets for main app content
import logoimage from "../assets/BCBLogo3-01.svg"
import footerimage from "../assets/BCBBanner.jpg"

// main app header and footer content
export default {
  name: 'app',
  data(){
    return {
      header: "Bike Coffee Bake",
      logoimage: logoimage,
      logoimgtext: "logo of bike wheel, chemex and bread",
      footerimgtext: "banner image of bikes, coffee and baked goods",
      footerimage: footerimage,
      subheader: "Est. 2021",
      footertext: "2021 BCB",
    }
  }
}

</script>


<style lang="scss">

*,
*::before,
*::after {
  box-sizing: border-box;
  margin: 0;
}

.button--green {
  display: inline-block;
  border-radius: 4px;
  border: 1px solid #3b8070;
  color: #3b8070;
  text-decoration: none;
  padding: 10px 30px;
}

.button--green:hover {
  color: #fff;
  background-color: #3b8070;
}

.button--grey {
  display: inline-block;
  border-radius: 4px;
  border: 1px solid #35495e;
  color: #35495e;
  text-decoration: none;
  padding: 10px 30px;
  margin-left: 15px;
}

.button--grey:hover {
  color: #fff;
  background-color: #35495e;
}
</style>
