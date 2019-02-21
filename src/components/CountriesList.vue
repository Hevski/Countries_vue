<template lang="html">
<div class="">
  <select v-on:change="handleChange">
    <option disable value=''>Select a country...</option>
    <option v-for="(country, index) in countries" :key="index" :value="index" >{{country.name}}</option>
  </select>
</div>
</template>

<script>
import {eventBus} from '../main.js'

export default {
  name: 'countries-list',
  props: ['countries'],
  methods: {
    handleChange(){
      eventBus.$emit('clicked-country', this.countries[event.target.value])
      console.log(this.countries[event.target.value]);
    }
  }
}
</script>

<style lang="css" scoped>
</style>
