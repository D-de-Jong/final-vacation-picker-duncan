<template>
  <h3 class="mt-4 text-light">
    Selected Destination:
  </h3>
    <ul class="list-group">
      <li class="list-group-item bg-dark text-light">
        {{country.id}}
      </li>
      <li class="list-group-item bg-dark text-light">
        <img :src="getImgUrl(country.img)" style="height: 20rem" alt="Picture of a country" class="img-fluid">
      </li>
      <li class="list-group-item bg-dark text-light">
        {{country.name}}
      </li>
      <li class="list-group-item bg-dark text-light">
        {{country.capital}}
      </li>
      <li class="list-group-item bg-dark text-light">
        {{country.cost}}
      </li>
      <li class="list-group-item bg-dark text-light ">
        {{country.details}}
      </li>

      <li v-if="isExpensive" class="list-group-item bg-dark text-light ">
        <p class="bg-danger">This vacation is too expensive</p>
      </li>
    </ul>
  <span class="justify-content-center">
        <button @click="setRating(1)">+1</button>
        <button @click="setRating(-1)">-1</button>
  </span>
  <span class="float-end" v-if="country.rating !== 0">{{country.rating}}</span>
</template>

<script>
import mixins from "@/mixins/mixins";

export default {
  name: "CountryDetail",
  props: ['country'],
  mixins: [mixins],
  methods: {
    onRating(rating){
      this.countryData.countries[this.selectedCountryIndex].rating += rating;
    },
    setRating(value){
      this.$emit('rating', value);
    },
    selectCountry(index) {
      console.warn('click');
      this.selectedCountryIndex = index;
      console.log(this.selectedCountryIndex);
    },
    getImgUrl(img){
      return require('../assets/countries/' +img)
    }
  },
  emits: ['rating'],
  computed:{
    isExpensive(){
      return this.country.cost > 1000
    }
  }
}

</script>

<style scoped>

</style>