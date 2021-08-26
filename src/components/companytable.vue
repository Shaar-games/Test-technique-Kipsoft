<template>
  <div class="container mx-auto" v-if="entreprises.etablissement">
    <div class="flex flex-col" >
      <div class="my-2 py-2 overflow-x-auto sm:-mx-6 sm:px-6 lg:-mx-8 lg:px-8">
        <div class="align-middle inline-block min-w-full overflow-hidden sm:rounded-lg border-b border-gray-200">
          <table class="min-w-full border-2 border-gray-200">
            <thead class="bg-white">
              <tr>
                <th class="px-6 py-3 border-b border-gray-200 bg-gray-50 text-left text-xs leading-4 font-medium text-gray-500 uppercase tracking-wider">
                  Nom
                </th>
                <th class="px-6 py-3 border-b border-gray-200 bg-gray-50 text-left text-xs leading-4 font-medium text-gray-500 uppercase tracking-wider">
                  Siret
                </th>
                <th class="px-6 py-3 border-b border-gray-200 bg-gray-50 text-left text-xs leading-4 font-medium text-gray-500 uppercase tracking-wider">
                  Région
                </th>
                <th class="px-6 py-3 border-b border-gray-200 bg-gray-50 text-left text-xs leading-4 font-medium text-gray-500 uppercase tracking-wider">
                  Activité principale
                </th>
              </tr>
            </thead>
            <tbody class="bg-white">
              <tr v-for="v in entreprises.etablissement" :key="v.id" class="cursor-pointer" @click="v.expanded = !v.expanded">
                <td class="px-6 py-4 whitespace-no-wrap border-b border-gray-200">
                  <div class="text-sm leading-5 font-medium text-gray-900">{{v.nom_raison_sociale}}</div>
                </td>
                <td class="px-6 py-4 whitespace-no-wrap border-b border-gray-200">
                  <div class="text-sm leading-5 font-medium text-gray-900">{{v.siret}}</div>
                  <div class="text-sm leading-5 text-gray-500">{{v.siren}}</div>
                </td>
                <td class="px-6 py-4 whitespace-no-wrap border-b border-gray-200">
                  <div class="text-sm leading-5 text-gray-900">{{v.geo_adresse}}</div>
                  <div class="text-sm leading-5 text-gray-500">{{generateaddr(v)}}</div>
                </td>
                <td class="px-6 py-4 whitespace-no-wrap border-b border-gray-200 text-sm leading-5 text-gray-500">
                  <div class="text-sm leading-5 text-gray-900">{{v.libelle_activite_principale}}</div>
                </td>
                <td class="px-6 py-4 whitespace-no-wrap text-right border-b border-gray-200 text-sm leading-5 font-medium">
                  <a href="#" class="text-indigo-600 hover:text-indigo-900 focus:outline-none focus:underline">...</a>
                </td>
              </tr>
            </tbody>
          </table>
        </div>
      </div>
    </div>
    <div class="content-center w-max float-right bg-white px-4 py-3 flex items-center justify-between border-t border-gray-200 sm:px-6">
      <div class="flex-1 flex justify-between sm:hidden">
        <div class="cursor-pointer relative inline-flex items-center px-4 py-2 border border-gray-300 text-sm font-medium rounded-md text-gray-700 bg-white hover:bg-gray-50">
        Previous
        </div>
        <div class="cursor-pointer ml-3 relative inline-flex items-center px-4 py-2 border border-gray-300 text-sm font-medium rounded-md text-gray-700 bg-white hover:bg-gray-50">
        Next
        </div>
      </div>
      <div class="hidden sm:flex-1 sm:flex sm:items-center sm:justify-between">
        <div>
          <p class="text-sm text-gray-700">
            Affichage de
            <span class="font-medium">{{entreprises.page * entreprises.per_page - entreprises.per_page + 1}}</span>
            à
            <span class="font-medium">{{Math.min(entreprises.page * entreprises.per_page , entreprises.total_results)}}</span>
            sur
            <span class="font-medium">{{entreprises.total_results}}</span>
            résultats
          </p>
        </div>
        <div>
          <nav class="cursor-pointer ml-10 relative z-0 inline-flex rounded-md shadow-sm -space-x-px" aria-label="Pagination">
            <div href="#" class="relative inline-flex items-center px-2 py-2 rounded-l-md border border-gray-300 bg-white text-sm font-medium text-gray-500 hover:bg-gray-50">
              <span class="sr-only">Previous</span>
              <!-- Heroicon name: solid/chevron-left -->
              <svg class="h-5 w-5" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20" fill="currentColor" aria-hidden="true">
                <path fill-rule="evenodd" d="M12.707 5.293a1 1 0 010 1.414L9.414 10l3.293 3.293a1 1 0 01-1.414 1.414l-4-4a1 1 0 010-1.414l4-4a1 1 0 011.414 0z" clip-rule="evenodd" />
              </svg>
            </div>
            <div v-if="true">

            </div>
            <div aria-current="page" class="cursor-pointer z-10 bg-indigo-50 border-indigo-500 text-indigo-600 relative inline-flex items-center px-4 py-2 border text-sm font-medium">
            1
            </div>
            <div class="cursor-pointer bg-white border-gray-300 text-gray-500 hover:bg-gray-50 relative inline-flex items-center px-4 py-2 border text-sm font-medium">
            2
            </div>
            <div class="cursor-pointer relative inline-flex items-center px-2 py-2 rounded-r-md border border-gray-300 bg-white text-sm font-medium text-gray-500 hover:bg-gray-50">
              <span class="sr-only">Next</span>
              <!-- Heroicon name: solid/chevron-right -->
              <svg class="h-5 w-5" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20" fill="currentColor" aria-hidden="true">
                <path fill-rule="evenodd" d="M7.293 14.707a1 1 0 010-1.414L10.586 10 7.293 6.707a1 1 0 011.414-1.414l4 4a1 1 0 010 1.414l-4 4a1 1 0 01-1.414 0z" clip-rule="evenodd" />
              </svg>
            </div>
          </nav>
        </div>
      </div>
    </div>
  </div>
  <div v-else>
    <div class="mt-10 mx-10 py-2" v-if="first != true">
      <h1 class="text-center font-large text-4xl my-2">😢</h1>
      <h1 class="text-center font-bold">Aucun résultat trouvé.</h1>
    </div>
    <div class="mt-10 mx-10 py-2" v-if="first == true">
      <h1 class="text-center font-large text-4xl my-2">🔍</h1>
      <h1 class="text-center font-bold">Dans la barre de recherche, entrez les premières lettres du nom du l'entreprise recherché.</h1>
    </div>
  </div>
</template>

<script>
export default {
  data : function(){
    return {
      first : true
    }
  },
  watch: {
    entreprises: {
      immediate: true, 
      handler () {
        this.first = false
      }
    }
  },
  mounted : function(){
    this.first = true
  },
  methods : {
    generateaddr : function(v){
      if( v.libelle_region && v.libelle_commune ){
        return v.libelle_region + ", " + v.libelle_commune
      }else if( v.libelle_region && !v.libelle_commune ){
        return v.libelle_region
      }else if( !v.libelle_region && v.libelle_commune){
        return v.libelle_commune
      }
      return ""
    }
  },
  props :{
    entreprises : Object
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
