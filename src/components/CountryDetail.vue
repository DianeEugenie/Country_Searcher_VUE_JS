<template lang="html">
  <div class="country-display">
    <h2>{{country.name}}</h2>
    <img :src="country.flag"></img>
    <p>Capital: {{country.capital}} <br />
    Population: {{country.population | toFormat}}</p>
    <h3>Languages:</h3>
    <span v-for="language of countriesLanguages">{{language}} </span>

  </div>
</template>

<script>
export default {
  name: 'country-detail',
  props: ['country'],
  computed: {
    countriesLanguages() {
      return this.country.languages.map((language) => {
        return language.name
      })
    }
  },
  filters: {
    toFormat(value) {
      return value.toLocaleString('en-GB');
    }
  }
}
</script>

<style lang="css" scoped>
  .country-display {
    display: flex;
    flex-direction: column;
    font-family: fantasy;
    padding: 0.3em;
    min-width: 590px;
    min-height: 400px;
    justify-content: center;
    align-items: center;
    border: 1px solid #8c826f;
    border-radius: 15px;
    background-color: #f0e4cc;
  }
  img {
    width: 100px;
    height: auto;
    margin: 0.5em;
  }
</style>
