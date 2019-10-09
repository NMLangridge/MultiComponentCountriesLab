<template lang="html">
  <div v-if='country'>
    <h3>{{country.name}}</h3>
    <p>Name: {{country.name}}</p>
    <p>Capital: {{country.capital}}</p>
    <p>Population: {{country.population}}</p>
  </div>
</template>

<script>
export default {
  name: 'country-detail',
  props: ['country']
}
</script>

<style lang="css" scoped>
</style>
