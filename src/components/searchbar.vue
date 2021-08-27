<template>
  <div class="container mx-auto text-center">
    <div class="pt-2 relative mx-auto text-gray-600 ">
      <input v-model="search" v-on:blur="$emit('search', search , 1)" v-on:keyup.enter="$emit('search', search , 1)" class="search shadow-2xl border-2 border-gray-300 bg-white h-10 px-5 pr-16 rounded-lg text-sm focus:outline-none" type="search" name="search" placeholder="Rechercher">
      <kbd aria-label="Rechercher" class="cursor-pointer mx-2" @click="$emit('search', search , 1)">🔍</kbd>
    </div>
  </div>
</template>

<script>
export default {
  data: function () {
    return {
      search: "",
      page : 1
    }
  }
}
</script>

<style scoped>
/* clears the ‘X’ from Internet Explorer */
input[type=search]::-ms-clear { display: none; width : 0; height: 0; }
input[type=search]::-ms-reveal { display: none; width : 0; height: 0; }
/* clears the ‘X’ from Chrome */
input[type="search"]::-webkit-search-decoration,
input[type="search"]::-webkit-search-cancel-button,
input[type="search"]::-webkit-search-results-button,
input[type="search"]::-webkit-search-results-decoration { display: none; }

@media screen and (max-width: 768px) { .search { width: 80%; }}
@media screen and (min-width: 768px) { .search { width: 50%; }}

</style>
