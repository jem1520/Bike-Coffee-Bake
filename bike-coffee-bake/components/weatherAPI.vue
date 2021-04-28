<template >
  <!--Weather API data component -->
  <div class="weather text-center">
    <p>{{weatherdata.lat  }}    {{  weatherdata.lon}}</p>
    <p>{{weatherdata.humidity}} {{weatherdata.pressure}}</p>
    <p>{{weatherdata.speed}}  {{weatherdata.deg}}</p>
  </div>
</template>

<script>
//props and validation for API data
export default {
      props: {
        weatherdata: [Array, Object, String, Number],
    }
}
</script>

<style lang="scss">
</style>
