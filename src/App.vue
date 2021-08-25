<template>
  <div class="space-y-10">
    <h1 class="text-center mt-10 title font-bold my-10">Test technique Kipsoft</h1>
  </div>
  <searchbar/>
  <companytable class="mt-10"/>
</template>

<script>
import searchbar from './components/searchbar.vue'
import companytable from './components/companytable.vue'

export default {
  name: 'App',
  components: {
    searchbar,
    companytable
  }
}
</script>

<style scoped>

@media screen and (max-width: 768px) { .title { font-size: 30px; }}
@media screen and (min-width: 768px) { .title { font-size: 35px; }}

</style>
