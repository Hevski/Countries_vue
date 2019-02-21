<template lang="html">
  <div>
    <h1>Countries</h1>
    <div class="main-container">
    <search-box :countries='countries'></search-box>
    <countries-list :countries='countries'></countries-list>
    <country-details :country='selectedCountry'></country-details>
    </div>
  </div>
</template>

<script>
import CountriesList from './components/CountriesList.vue';
import CountryDetails from './components/CountryDetails.vue';
import SearchBox from './components/SearchBox.vue';
import {eventBus} from './main.js';


export default {
  data(){
    return {
      countries: [],
      selectedCountry: null
    }
  },
  components: {
    "countries-list": CountriesList,
    "country-details": CountryDetails,
    "search-box": SearchBox
  },
  mounted(){
    fetch('https://restcountries.eu/rest/v2/all')
    .then(res => res.json())
    .then(countries => this.countries = countries)
    eventBus.$on('clicked-country', (country) => {
      this.selectedCountry = country
    })
  }
}
</script>

<style lang="css" scoped>
  h1 {
    text-align: center;
  }
  .main-container {
    display: flex;
    justify-content: space-between;
  }
</style>
