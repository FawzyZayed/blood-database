<template>
  <div class="home">
    <!-- <select name="" @change="onChange($event)">
      <option value="" disabled selected>select country</option>
      <option v-for="(country, index) in citiesName" :key="index" :value="country.id">{{ country.country }}</option>
    </select>
    <select name="" id="">
      <option value="" selected>select country first</option>
      <option v-for="(city, index) in currentCities" :key="index">{{ city.cityName }}</option>
    </select> -->
    <v-select
      label="Sellect Country"
      :items="countries"
      :filter="clickme"
      item-text="name"
      item-value="iso3"
      return-object
      single-line
    ></v-select>
  </div>
</template>

<script>
// @ is an alias to /src
import countries from '../assets/jsons/countries.json'
import axios from 'axios'

export default {
  name: 'home',
  data () {
    return {
      countries: []
    }
  },
  methods: {
    clickme (event) {
      console.log(event)
    }
    // onChange (event) {
    //   // console.log(event.target.value)
    //   let cityId = event.target.value
    //   // console.log(this.citiesName[cityId].cities)
    //   this.currentCities = []
    //   const data = this.citiesName[cityId].cities
    //   for (let key in data) {
    //     const cityName = data[key]
    //     this.currentCities.push({ cityName })
    //   }
    //   console.log(this.currentCities)
    // }
  },
  created () {
    countries.forEach((element, index) => {
      console.log(element, index)
      this.countries.push({ id: index, name: element.name, states: element.states, iso3: element.iso3 })
    })
    console.log(this.countries)
  }
}
</script>
