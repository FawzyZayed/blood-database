<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png">
    <HelloWorld msg="Welcome to Your Vue.js App"/>
    <select name="" id="">
      <option value="" disabled selected>select country</option>
      <option v-for="(country, index) in countriesName" :key="index">{{ country }}</option>
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
      countriesName: []
    }
  },
  components: {
    HelloWorld
  },
  created () {
    countries.forEach((element, index, array) => {
      this.countriesName.push(element.name)
      console.log(element.states)
    })
  }
}
</script>
