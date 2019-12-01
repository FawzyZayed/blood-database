<template>
  <div class="home">
    <b-container class="bv-example-row">
      <b-row>
        <b-col>
          <b-form-select
            class="mb-3"
            :options="citiesName"
            @change="onChange"
            value-field="id"
            text-field="country"
            v-model="thisCountry"
            >
          </b-form-select>
        </b-col>
        <b-col>
          <b-form-select
            class="mb-3"
            :options="currentCities"
            value-field="id"
            text-field="cityName"
            v-model="thisCity"
          >
          </b-form-select>
        </b-col>
        <b-col>
          <b-form-select
            class="mb-3"
            :options="bloodtype"
            v-model="thisBlood"
          >
          </b-form-select>
        </b-col>
        <b-col>
          <b-button variant="outline-primary">Search</b-button>
        </b-col>
      </b-row>
    </b-container>
  </div>
</template>

<script>
// @ is an alias to /src
// import HelloWorld from '@/components/HelloWorld.vue'
import axios from 'axios'

export default {
  name: 'home',
  data () {
    return {
      thisCountry: '0',
      thisCity: '246-0',
      thisBlood: 'A+',
      countriesName: [],
      citiesName: [],
      currentCities: [],
      bloodtype: ['A+', 'A-']
    }
  },

  methods: {
    onChange (event, index) {
      // console.log(event)
      let cityId = event
      // console.log(this.citiesName[cityId].cities)
      this.currentCities = []
      const data = this.citiesName[cityId].cities
      for (let key in data) {
        const cityName = data[key]
        this.currentCities.push({ id: cityId + '-' + [key], cityName })
      }
      this.thisCity = cityId + '-0'
      // console.log(this.currentCities)
    }
  },
  created () {
    this.axios.get('https://gblooddb.firebaseio.com/countries.json').then(response => {
      // console.log(response.data)
      const data = response.data
      data.forEach((element, index, array) => {
        this.countriesName.push({ id: index, country: element.name })
        this.citiesName.push({ id: index, country: element.name, iso3: element.iso3, cities: element.states })
        this.currentCities = []
        const nwdata = this.citiesName[index].cities
        for (let key in nwdata) {
          const cityName = nwdata[key]
          this.currentCities.push({ id: index + '-' + [key], cityName })
        }
      })
    })
  }
}
</script>
