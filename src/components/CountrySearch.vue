<template lang="html">

  <input @input="onInput" type="text" v-model="nameCountry" value="">

</template>

<script>
import {eventBus} from '../main.js'
export default {
  name: 'country-search',
  data(){
    return {
      nameCountry: null
    }
  },
  props: ['countries'],
  methods: {
    onInput() {
        let searchedName = this.nameCountry.toLowerCase();

        for (let country of this.countries) {
          let countryName = country.name.toLowerCase();

          if (countryName.indexOf(searchedName) > -1) {
            return eventBus.$emit('country-selected', country)
        }
      }
    }
  }

}
</script>

<style lang="css" scoped>
input {
  max-width: 20em;
  padding: 0.5em;
  font-family: fantasy;
  font-size: 1em;
  border-radius: 5px;
  border: 2px solid lightseagreen;
  text-align: center;
  margin-bottom: 1.5em;
  background-color: #f7f4ed;
}
</style>
