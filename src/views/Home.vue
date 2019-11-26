<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png">
    <HelloWorld msg="Welcome to Your Vue.js App"/>
    <select name="" @change="onChange($event)">
      <option value="" disabled selected>select country</option>
      <option v-for="(country, index) in citiesName" :key="index" :value="country.id">{{ country.country }}</option>
    </select>
    <select name="" id="">
      <!-- <option value="" selected>select country first</option> -->
      <option v-for="(city, index) in currentCities" :key="index">{{ city }}</option>
    </select>
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue'
import countries from '../assets/jsons/countries.json'
import axios from 'axios'

export default {
  name: 'home',
  data () {
    return {
      countriesName: [],
      citiesName: [],
      currentCities: []
    }
  },
  components: {
    HelloWorld
  },
  methods: {
    onChange (event) {
      // console.log(event.target.value)
      let cityId = event.target.value
      // console.log(this.citiesName[cityId].cities)
      this.currentCities = []
      this.currentCities.push(this.citiesName[cityId].cities)
      console.log(this.currentCities)
    }
  },
  created () {
    countries.forEach((element, index, array) => {
      this.countriesName.push({ id: index, country: element.name })
      this.citiesName.push({ id: index, country: element.name, cities: element.states })
    })
  }
}
</script>
