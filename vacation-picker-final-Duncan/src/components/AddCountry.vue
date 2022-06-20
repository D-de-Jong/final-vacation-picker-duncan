<template>
  <h2 class="mt-4 text-light">
    Add a new destination
  </h2>
  <input type="text" v-model="newCountry"/> <button class="btn btn-secondary" @click="addCountry()">Add</button>
  <h3 class="text-light">
    {{newCountry}}
  </h3>
  <ul class="list-group">
    <li class="list-group-item bg-dark text-light" v-for="(country, index) in newCountries" :key="index">
      {{country}}
    </li>
  </ul>
</template>

<script>

import index from "@/router";

export default {
  name: "AddCountry",
  data(){
    return {
      index,
      newCountry:"",
      newCountries:[]
    }
  },
  methods: {
    addCountry(){
      this.newCountries.push(this.newCountry);
      this.newCountry = " ";
    },
  }
}

</script>

<style scoped>

</style>