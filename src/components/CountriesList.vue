<template lang="html">
<div class="">
  <select v-on:change="handleChange" v-model="selectedCountryIndex">
    <option disable value=''>Select a country...</option>
    <option v-for="(country, index) in countries" :key="index" :value="index" >{{country.name}}</option>
  </select>
</div>
</template>

<script>
import {eventBus} from '../main.js'

export default {
  name: 'countries-list',
  data(){
  return {
    selectedCountryIndex: ''

  }
},
  props: ['countries'],
  methods: {
    handleChange(){
      eventBus.$emit('clicked-country', this.selectedCountryIndex)
    }
  }
}
</script>

<style lang="css" scoped>
</style>
