<template lang="html">
  <div>
    <h1>Countries</h1>
    <div class="main-container">
      <!-- <countries-list :countries='countries'></countries-list> -->

      <label for="country_select">Select a Country:</label>
      <select id="country_select" v-model="selectedCountry">
        <option disabled value="">Select a Country</option>
        <option v-for="country in countries" :value="country">{{country.name}}</option>
      </select>

      <country-detail :country='selectedCountry'></country-detail>

    </div>
  </div>
</template>

<script>
import { eventBus } from './main.js';
import CountriesList from './components/CountriesList.vue';
import CountryDetail from './components/CountryDetail.vue';

export default {
  name: 'app',
  data(){
    return {
      countries: [],
      selectedCountry: null
    };
  },
  mounted(){
    fetch('https://restcountries.eu/rest/v2/all')
    .then(result => result.json())
    .then(countries => this.countries = countries)

    eventBus.$on('country-selected', (country) => {
      this.selectedCountry = country;
    })
  },
  components: {
    "countries-list": CountriesList,
    "country-detail": CountryDetail
  }
}
</script>

<style lang="css" scoped>
  .main-container {
    display: flex;
    justify-content: flex-start;
  }
</style>
