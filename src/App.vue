<template>
  <div class="space-y-10">
    <h1 class="text-center mt-10 title font-bold my-10">Test technique Kipsoft</h1>
  </div>
  <searchbar v-on:search="UpdateSearch"/>
  <companytable  v-bind:entreprises="entreprises" class="mt-10"/>
</template>

<script>

const axios = require('axios');

import searchbar from './components/searchbar.vue'
import companytable from './components/companytable.vue'

export default {
  name: 'App',
  components: {
    searchbar,
    companytable
  },
  methods:{
    UpdateSearch : async function (value , page) {
      console.log( value , page )
      try{
        let rep = await axios.get( `https://entreprise.data.gouv.fr/api/sirene/v1/full_text/${value}?per_page=5&page=${page}` )

        this.entreprises = rep.data
        console.log( "updated with " , value)
        console.log( this.entreprises )
      }catch(e){
        this.entreprises = {}
      }
    }
  },
  mounted : function() {
    
  },
  data: function () {
    return {
      entreprises : {}
    }
  }
}
</script>

<style scoped>

@media screen and (max-width: 768px) { .title { font-size: 30px; }}
@media screen and (min-width: 768px) { .title { font-size: 35px; }}

</style>
