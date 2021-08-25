<template>
  <div class="container mx-auto">
    <div class="flex flex-col">
      <div class="-my-2 py-2 overflow-x-auto sm:-mx-6 sm:px-6 lg:-mx-8 lg:px-8">
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
              <tr v-for="v in entreprises.etablissement" :key="v.id">
                <td class="px-6 py-4 whitespace-no-wrap border-b border-gray-200">
                    <div class="text-sm leading-5 font-medium text-gray-900">{{v.nom_raison_sociale}}</div>
                    <div class="text-sm leading-5 text-gray-500">{{v.siren}}</div>
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

            <div class="bg-white px-4 py-3 flex items-center justify-between border-t border-gray-200 sm:px-6">
  <div class="flex-1 flex justify-between sm:hidden">
    <a href="#" class="relative inline-flex items-center px-4 py-2 border border-gray-300 text-sm font-medium rounded-md text-gray-700 bg-white hover:bg-gray-50">
      Previous
    </a>
    <a href="#" class="ml-3 relative inline-flex items-center px-4 py-2 border border-gray-300 text-sm font-medium rounded-md text-gray-700 bg-white hover:bg-gray-50">
      Next
    </a>
  </div>
  <div class="hidden sm:flex-1 sm:flex sm:items-center sm:justify-between">
    <div>
      <p class="text-sm text-gray-700">
        Showing
        <span class="font-medium">1</span>
        to
        <span class="font-medium">10</span>
        of
        <span class="font-medium">97</span>
        results
      </p>
    </div>
    <div>
      <nav class="relative z-0 inline-flex rounded-md shadow-sm -space-x-px" aria-label="Pagination">
        <a href="#" class="relative inline-flex items-center px-2 py-2 rounded-l-md border border-gray-300 bg-white text-sm font-medium text-gray-500 hover:bg-gray-50">
          <span class="sr-only">Previous</span>
          <!-- Heroicon name: solid/chevron-left -->
          <svg class="h-5 w-5" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20" fill="currentColor" aria-hidden="true">
            <path fill-rule="evenodd" d="M12.707 5.293a1 1 0 010 1.414L9.414 10l3.293 3.293a1 1 0 01-1.414 1.414l-4-4a1 1 0 010-1.414l4-4a1 1 0 011.414 0z" clip-rule="evenodd" />
          </svg>
        </a>
        <!-- Current: "z-10 bg-indigo-50 border-indigo-500 text-indigo-600", Default: "bg-white border-gray-300 text-gray-500 hover:bg-gray-50" -->
        <a href="#" aria-current="page" class="z-10 bg-indigo-50 border-indigo-500 text-indigo-600 relative inline-flex items-center px-4 py-2 border text-sm font-medium">
          1
        </a>
        <a href="#" class="bg-white border-gray-300 text-gray-500 hover:bg-gray-50 relative inline-flex items-center px-4 py-2 border text-sm font-medium">
          2
        </a>
        <a href="#" class="bg-white border-gray-300 text-gray-500 hover:bg-gray-50 hidden md:inline-flex relative items-center px-4 py-2 border text-sm font-medium">
          3
        </a>
        <span class="relative inline-flex items-center px-4 py-2 border border-gray-300 bg-white text-sm font-medium text-gray-700">
          ...
        </span>
        <a href="#" class="bg-white border-gray-300 text-gray-500 hover:bg-gray-50 hidden md:inline-flex relative items-center px-4 py-2 border text-sm font-medium">
          8
        </a>
        <a href="#" class="bg-white border-gray-300 text-gray-500 hover:bg-gray-50 relative inline-flex items-center px-4 py-2 border text-sm font-medium">
          9
        </a>
        <a href="#" class="bg-white border-gray-300 text-gray-500 hover:bg-gray-50 relative inline-flex items-center px-4 py-2 border text-sm font-medium">
          10
        </a>
        <a href="#" class="relative inline-flex items-center px-2 py-2 rounded-r-md border border-gray-300 bg-white text-sm font-medium text-gray-500 hover:bg-gray-50">
          <span class="sr-only">Next</span>
          <!-- Heroicon name: solid/chevron-right -->
          <svg class="h-5 w-5" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20" fill="currentColor" aria-hidden="true">
            <path fill-rule="evenodd" d="M7.293 14.707a1 1 0 010-1.414L10.586 10 7.293 6.707a1 1 0 011.414-1.414l4 4a1 1 0 010 1.414l-4 4a1 1 0 01-1.414 0z" clip-rule="evenodd" />
          </svg>
        </a>
      </nav>
    </div>
  </div>
</div>
          </table>

          
        </div>
      </div>
    </div>
  </div>

  
</template>

<script>
export default {
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
  data: function () {
    return {
      entreprises:{
  "total_results": 732,
  "total_pages": 147,
  "per_page": 5,
  "page": "1",
  "etablissement": [
    {
      "id": 181689998,
      "siren": "898486436",
      "siret": "89848643600014",
      "nic": "00014",
      "l1_normalisee": "SALUTATIONS AUDIO",
      "l2_normalisee": "SALUTATIONS",
      "l3_normalisee": null,
      "l4_normalisee": "32 RUE LA FONTAINE",
      "l5_normalisee": null,
      "l6_normalisee": "92350 LE PLESSIS-ROBINSON",
      "l7_normalisee": null,
      "l1_declaree": "SALUTATIONS",
      "l2_declaree": null,
      "l3_declaree": null,
      "l4_declaree": "32 RUE LA FONTAINE",
      "l5_declaree": null,
      "l6_declaree": "92350 LE PLESSIS-ROBINSON",
      "l7_declaree": null,
      "numero_voie": "32",
      "indice_repetition": null,
      "type_voie": "RUE",
      "libelle_voie": "LA FONTAINE",
      "code_postal": "92350",
      "cedex": null,
      "region": "11",
      "libelle_region": "Île-de-France",
      "departement": "92",
      "arrondissement": "1",
      "canton": "06",
      "commune": "060",
      "libelle_commune": "PLESSIS ROBINSON (LE)",
      "departement_unite_urbaine": "92",
      "taille_unite_urbaine": "8",
      "numero_unite_urbaine": "00851",
      "etablissement_public_cooperation_intercommunale": "200054781",
      "tranche_commune_detaillee": "42",
      "zone_emploi": "1101",
      "is_siege": "1",
      "enseigne": null,
      "indicateur_champ_publipostage": "A",
      "statut_prospection": null,
      "date_introduction_base_diffusion": "202104",
      "nature_entrepreneur_individuel": null,
      "libelle_nature_entrepreneur_individuel": null,
      "activite_principale": "5911A",
      "libelle_activite_principale": "Production de films et de programmes pour la télévision",
      "date_validite_activite_principale": null,
      "tranche_effectif_salarie": null,
      "libelle_tranche_effectif_salarie": null,
      "tranche_effectif_salarie_centaine_pret": null,
      "date_validite_effectif_salarie": null,
      "origine_creation": null,
      "date_creation": "20210410",
      "date_debut_activite": "20210410",
      "nature_activite": null,
      "lieu_activite": null,
      "type_magasin": null,
      "is_saisonnier": null,
      "modalite_activite_principale": null,
      "caractere_productif": null,
      "participation_particuliere_production": null,
      "caractere_auxiliaire": null,
      "nom_raison_sociale": "SALUTATIONS AUDIO",
      "sigle": null,
      "nom": null,
      "prenom": null,
      "civilite": null,
      "numero_rna": null,
      "nic_siege": "00014",
      "region_siege": "11",
      "departement_commune_siege": "92060",
      "email": null,
      "nature_juridique_entreprise": "5710",
      "libelle_nature_juridique_entreprise": "SAS, société par actions simplifiée",
      "activite_principale_entreprise": "5911A",
      "libelle_activite_principale_entreprise": "Production de films et de programmes pour la télévision",
      "date_validite_activite_principale_entreprise": null,
      "activite_principale_registre_metier": null,
      "is_ess": null,
      "date_ess": null,
      "tranche_effectif_salarie_entreprise": null,
      "libelle_tranche_effectif_salarie_entreprise": null,
      "tranche_effectif_salarie_entreprise_centaine_pret": null,
      "date_validite_effectif_salarie_entreprise": null,
      "categorie_entreprise": null,
      "date_creation_entreprise": "202104",
      "date_introduction_base_diffusion_entreprise": "202104",
      "indice_monoactivite_entreprise": null,
      "modalite_activite_principale_entreprise": null,
      "caractere_productif_entreprise": null,
      "date_validite_rubrique_niveau_entreprise_esa": null,
      "tranche_chiffre_affaire_entreprise_esa": null,
      "activite_principale_entreprise_esa": null,
      "premiere_activite_secondaire_entreprise_esa": null,
      "deuxieme_activite_secondaire_entreprise_esa": null,
      "troisieme_activite_secondaire_entreprise_esa": null,
      "quatrieme_activite_secondaire_entreprise_esa": null,
      "nature_mise_a_jour": null,
      "indicateur_mise_a_jour_1": null,
      "indicateur_mise_a_jour_2": null,
      "indicateur_mise_a_jour_3": null,
      "date_mise_a_jour": "2021-04-23T08:46:26",
      "created_at": "2021-07-04T02:05:15.000+02:00",
      "updated_at": "2021-07-04T02:05:15.000+02:00",
      "longitude": "2.268038",
      "latitude": "48.776799",
      "geo_score": "0.97",
      "geo_type": "housenumber",
      "geo_adresse": "32 Rue la Fontaine 92350 Le Plessis-Robinson",
      "geo_id": "92060_5110_00032",
      "geo_ligne": "G",
      "geo_l4": "32 RUE LA FONTAINE",
      "geo_l5": null
    },
    {
      "id": 179487660,
      "siren": "399366012",
      "siret": "39936601200017",
      "nic": "00017",
      "l1_normalisee": "SALUTERRE",
      "l2_normalisee": null,
      "l3_normalisee": null,
      "l4_normalisee": "26 RUE FEUTRIER",
      "l5_normalisee": null,
      "l6_normalisee": "75018 PARIS 18",
      "l7_normalisee": null,
      "l1_declaree": null,
      "l2_declaree": null,
      "l3_declaree": null,
      "l4_declaree": "26 RUE FEUTRIER",
      "l5_declaree": null,
      "l6_declaree": "75018 PARIS 18",
      "l7_declaree": null,
      "numero_voie": "26",
      "indice_repetition": null,
      "type_voie": "RUE",
      "libelle_voie": "FEUTRIER",
      "code_postal": "75018",
      "cedex": null,
      "region": "11",
      "libelle_region": null,
      "departement": "75",
      "arrondissement": "1",
      "canton": null,
      "commune": "118",
      "libelle_commune": "PARIS 18E ARRONDISSEMENT",
      "departement_unite_urbaine": null,
      "taille_unite_urbaine": null,
      "numero_unite_urbaine": null,
      "etablissement_public_cooperation_intercommunale": null,
      "tranche_commune_detaillee": "80",
      "zone_emploi": null,
      "is_siege": "1",
      "enseigne": null,
      "indicateur_champ_publipostage": "A",
      "statut_prospection": null,
      "date_introduction_base_diffusion": "200801",
      "nature_entrepreneur_individuel": null,
      "libelle_nature_entrepreneur_individuel": null,
      "activite_principale": "9001Z",
      "libelle_activite_principale": "Arts du spectacle vivant",
      "date_validite_activite_principale": null,
      "tranche_effectif_salarie": "NN",
      "libelle_tranche_effectif_salarie": null,
      "tranche_effectif_salarie_centaine_pret": null,
      "date_validite_effectif_salarie": null,
      "origine_creation": null,
      "date_creation": "19941001",
      "date_debut_activite": "20080101",
      "nature_activite": null,
      "lieu_activite": null,
      "type_magasin": null,
      "is_saisonnier": null,
      "modalite_activite_principale": null,
      "caractere_productif": null,
      "participation_particuliere_production": null,
      "caractere_auxiliaire": null,
      "nom_raison_sociale": "SALUTERRE",
      "sigle": null,
      "nom": null,
      "prenom": null,
      "civilite": null,
      "numero_rna": "W751117282",
      "nic_siege": "00017",
      "region_siege": "11",
      "departement_commune_siege": "75118",
      "email": null,
      "nature_juridique_entreprise": "9220",
      "libelle_nature_juridique_entreprise": "Association déclarée",
      "activite_principale_entreprise": "9001Z",
      "libelle_activite_principale_entreprise": "Arts du spectacle vivant",
      "date_validite_activite_principale_entreprise": null,
      "activite_principale_registre_metier": null,
      "is_ess": null,
      "date_ess": null,
      "tranche_effectif_salarie_entreprise": "NN",
      "libelle_tranche_effectif_salarie_entreprise": null,
      "tranche_effectif_salarie_entreprise_centaine_pret": null,
      "date_validite_effectif_salarie_entreprise": null,
      "categorie_entreprise": null,
      "date_creation_entreprise": "199410",
      "date_introduction_base_diffusion_entreprise": "201601",
      "indice_monoactivite_entreprise": null,
      "modalite_activite_principale_entreprise": null,
      "caractere_productif_entreprise": null,
      "date_validite_rubrique_niveau_entreprise_esa": null,
      "tranche_chiffre_affaire_entreprise_esa": null,
      "activite_principale_entreprise_esa": null,
      "premiere_activite_secondaire_entreprise_esa": null,
      "deuxieme_activite_secondaire_entreprise_esa": null,
      "troisieme_activite_secondaire_entreprise_esa": null,
      "quatrieme_activite_secondaire_entreprise_esa": null,
      "nature_mise_a_jour": null,
      "indicateur_mise_a_jour_1": null,
      "indicateur_mise_a_jour_2": null,
      "indicateur_mise_a_jour_3": null,
      "date_mise_a_jour": "2008-01-04T19:08:06",
      "created_at": "2021-07-04T01:47:22.000+02:00",
      "updated_at": "2021-07-04T01:47:22.000+02:00",
      "longitude": "2.346038",
      "latitude": "48.887029",
      "geo_score": "0.98",
      "geo_type": "housenumber",
      "geo_adresse": "26 Rue Feutrier 75018 Paris",
      "geo_id": "75118_3632_00026",
      "geo_ligne": "G",
      "geo_l4": "26 RUE FEUTRIER",
      "geo_l5": null
    },
    {
      "id": 172476719,
      "siren": "481172302",
      "siret": "48117230200053",
      "nic": "00053",
      "l1_normalisee": "SALUTERRE",
      "l2_normalisee": null,
      "l3_normalisee": null,
      "l4_normalisee": "32 CHEMIN DE RIBEBON",
      "l5_normalisee": null,
      "l6_normalisee": "24230 SAINT-ANTOINE-DE-BREUILH",
      "l7_normalisee": null,
      "l1_declaree": null,
      "l2_declaree": null,
      "l3_declaree": null,
      "l4_declaree": "32 CHEMIN DE RIBEBON",
      "l5_declaree": null,
      "l6_declaree": "24230 SAINT-ANTOINE-DE-BREUILH",
      "l7_declaree": null,
      "numero_voie": "32",
      "indice_repetition": null,
      "type_voie": "CHE",
      "libelle_voie": "DE RIBEBON",
      "code_postal": "24230",
      "cedex": null,
      "region": "75",
      "libelle_region": "Nouvelle-Aquitaine",
      "departement": "24",
      "arrondissement": "1",
      "canton": "11",
      "commune": "370",
      "libelle_commune": "SAINT ANTOINE DE BREUILH",
      "departement_unite_urbaine": "24",
      "taille_unite_urbaine": "5",
      "numero_unite_urbaine": "00553",
      "etablissement_public_cooperation_intercommunale": "200034197",
      "tranche_commune_detaillee": "14",
      "zone_emploi": "7201",
      "is_siege": "1",
      "enseigne": null,
      "indicateur_champ_publipostage": "A",
      "statut_prospection": null,
      "date_introduction_base_diffusion": "202008",
      "nature_entrepreneur_individuel": null,
      "libelle_nature_entrepreneur_individuel": null,
      "activite_principale": "7112B",
      "libelle_activite_principale": "Ingénierie, études techniques",
      "date_validite_activite_principale": null,
      "tranche_effectif_salarie": null,
      "libelle_tranche_effectif_salarie": null,
      "tranche_effectif_salarie_centaine_pret": null,
      "date_validite_effectif_salarie": null,
      "origine_creation": null,
      "date_creation": "20200801",
      "date_debut_activite": "20200801",
      "nature_activite": null,
      "lieu_activite": null,
      "type_magasin": null,
      "is_saisonnier": null,
      "modalite_activite_principale": null,
      "caractere_productif": null,
      "participation_particuliere_production": null,
      "caractere_auxiliaire": null,
      "nom_raison_sociale": "SALUTERRE",
      "sigle": null,
      "nom": null,
      "prenom": null,
      "civilite": null,
      "numero_rna": null,
      "nic_siege": "00053",
      "region_siege": "75",
      "departement_commune_siege": "24370",
      "email": null,
      "nature_juridique_entreprise": "5460",
      "libelle_nature_juridique_entreprise": "Autre SARL coopérative",
      "activite_principale_entreprise": "7112B",
      "libelle_activite_principale_entreprise": "Ingénierie, études techniques",
      "date_validite_activite_principale_entreprise": null,
      "activite_principale_registre_metier": null,
      "is_ess": null,
      "date_ess": null,
      "tranche_effectif_salarie_entreprise": "02",
      "libelle_tranche_effectif_salarie_entreprise": null,
      "tranche_effectif_salarie_entreprise_centaine_pret": null,
      "date_validite_effectif_salarie_entreprise": "2018",
      "categorie_entreprise": "PME",
      "date_creation_entreprise": "200412",
      "date_introduction_base_diffusion_entreprise": "202008",
      "indice_monoactivite_entreprise": null,
      "modalite_activite_principale_entreprise": null,
      "caractere_productif_entreprise": null,
      "date_validite_rubrique_niveau_entreprise_esa": null,
      "tranche_chiffre_affaire_entreprise_esa": null,
      "activite_principale_entreprise_esa": null,
      "premiere_activite_secondaire_entreprise_esa": null,
      "deuxieme_activite_secondaire_entreprise_esa": null,
      "troisieme_activite_secondaire_entreprise_esa": null,
      "quatrieme_activite_secondaire_entreprise_esa": null,
      "nature_mise_a_jour": null,
      "indicateur_mise_a_jour_1": null,
      "indicateur_mise_a_jour_2": null,
      "indicateur_mise_a_jour_3": null,
      "date_mise_a_jour": "2020-09-28T12:36:43",
      "created_at": "2021-07-04T00:51:32.000+02:00",
      "updated_at": "2021-07-04T00:51:32.000+02:00",
      "longitude": "0.111287",
      "latitude": "44.830841",
      "geo_score": "0.95",
      "geo_type": "housenumber",
      "geo_adresse": "32 Chemin de Ribebon 24230 Saint-Antoine-de-Breuilh",
      "geo_id": "24370_0140_00032",
      "geo_ligne": "G",
      "geo_l4": "32 CHEMIN DE RIBEBON",
      "geo_l5": null
    },
    {
      "id": 174511042,
      "siren": "841029572",
      "siret": "84102957200010",
      "nic": "00010",
      "l1_normalisee": "SALUTERRE",
      "l2_normalisee": null,
      "l3_normalisee": null,
      "l4_normalisee": "725 CHEMIN DU VINTUN",
      "l5_normalisee": null,
      "l6_normalisee": "38110 DOLOMIEU",
      "l7_normalisee": null,
      "l1_declaree": null,
      "l2_declaree": null,
      "l3_declaree": null,
      "l4_declaree": "725 CHEMIN DU VINTUN",
      "l5_declaree": null,
      "l6_declaree": "38110 DOLOMIEU",
      "l7_declaree": null,
      "numero_voie": "725",
      "indice_repetition": null,
      "type_voie": "CHE",
      "libelle_voie": "DU VINTUN",
      "code_postal": "38110",
      "cedex": null,
      "region": "84",
      "libelle_region": "Auvergne-Rhône-Alpes",
      "departement": "38",
      "arrondissement": "2",
      "canton": "24",
      "commune": "148",
      "libelle_commune": "DOLOMIEU",
      "departement_unite_urbaine": "38",
      "taille_unite_urbaine": "3",
      "numero_unite_urbaine": "38129",
      "etablissement_public_cooperation_intercommunale": "200068567",
      "tranche_commune_detaillee": "17",
      "zone_emploi": "8209",
      "is_siege": "1",
      "enseigne": null,
      "indicateur_champ_publipostage": "A",
      "statut_prospection": null,
      "date_introduction_base_diffusion": "201806",
      "nature_entrepreneur_individuel": null,
      "libelle_nature_entrepreneur_individuel": null,
      "activite_principale": "6630Z",
      "libelle_activite_principale": "Gestion de fonds",
      "date_validite_activite_principale": null,
      "tranche_effectif_salarie": null,
      "libelle_tranche_effectif_salarie": null,
      "tranche_effectif_salarie_centaine_pret": null,
      "date_validite_effectif_salarie": null,
      "origine_creation": null,
      "date_creation": "20180621",
      "date_debut_activite": "20180621",
      "nature_activite": null,
      "lieu_activite": null,
      "type_magasin": null,
      "is_saisonnier": null,
      "modalite_activite_principale": null,
      "caractere_productif": null,
      "participation_particuliere_production": null,
      "caractere_auxiliaire": null,
      "nom_raison_sociale": "SALUTERRE",
      "sigle": null,
      "nom": null,
      "prenom": null,
      "civilite": null,
      "numero_rna": null,
      "nic_siege": "00010",
      "region_siege": "84",
      "departement_commune_siege": "38148",
      "email": null,
      "nature_juridique_entreprise": "5499",
      "libelle_nature_juridique_entreprise": "Société à responsabilité limitée (sans autre indication)",
      "activite_principale_entreprise": "6630Z",
      "libelle_activite_principale_entreprise": "Gestion de fonds",
      "date_validite_activite_principale_entreprise": null,
      "activite_principale_registre_metier": null,
      "is_ess": null,
      "date_ess": null,
      "tranche_effectif_salarie_entreprise": null,
      "libelle_tranche_effectif_salarie_entreprise": null,
      "tranche_effectif_salarie_entreprise_centaine_pret": null,
      "date_validite_effectif_salarie_entreprise": null,
      "categorie_entreprise": "PME",
      "date_creation_entreprise": "201806",
      "date_introduction_base_diffusion_entreprise": "201806",
      "indice_monoactivite_entreprise": null,
      "modalite_activite_principale_entreprise": null,
      "caractere_productif_entreprise": null,
      "date_validite_rubrique_niveau_entreprise_esa": null,
      "tranche_chiffre_affaire_entreprise_esa": null,
      "activite_principale_entreprise_esa": null,
      "premiere_activite_secondaire_entreprise_esa": null,
      "deuxieme_activite_secondaire_entreprise_esa": null,
      "troisieme_activite_secondaire_entreprise_esa": null,
      "quatrieme_activite_secondaire_entreprise_esa": null,
      "nature_mise_a_jour": null,
      "indicateur_mise_a_jour_1": null,
      "indicateur_mise_a_jour_2": null,
      "indicateur_mise_a_jour_3": null,
      "date_mise_a_jour": "2018-07-13T07:12:41",
      "created_at": "2021-07-04T01:07:39.000+02:00",
      "updated_at": "2021-07-04T01:07:39.000+02:00",
      "longitude": "5.497244",
      "latitude": "45.635594",
      "geo_score": "0.95",
      "geo_type": "housenumber",
      "geo_adresse": "725 Chemin du Vintun 38110 Dolomieu",
      "geo_id": "38148_0920_00725",
      "geo_ligne": "G",
      "geo_l4": "725 CHEMIN DU VINTUN",
      "geo_l5": null
    },
    {
      "id": 174634519,
      "siren": "813994886",
      "siret": "81399488600014",
      "nic": "00014",
      "l1_normalisee": "MADAME EMILIE PETELAZ SALUTE",
      "l2_normalisee": null,
      "l3_normalisee": null,
      "l4_normalisee": "27 AVENUE JEAN JAURES",
      "l5_normalisee": null,
      "l6_normalisee": "38400 SAINT MARTIN D'HERES",
      "l7_normalisee": null,
      "l1_declaree": "PUP SOINS",
      "l2_declaree": null,
      "l3_declaree": null,
      "l4_declaree": "27 AVENUE JEAN JAURES",
      "l5_declaree": null,
      "l6_declaree": "38400 SAINT MARTIN D'HERES",
      "l7_declaree": null,
      "numero_voie": "27",
      "indice_repetition": null,
      "type_voie": "AV",
      "libelle_voie": "JEAN JAURES",
      "code_postal": "38400",
      "cedex": null,
      "region": "84",
      "libelle_region": "Auvergne-Rhône-Alpes",
      "departement": "38",
      "arrondissement": "1",
      "canton": "22",
      "commune": "421",
      "libelle_commune": "SAINT MARTIN D'HERES",
      "departement_unite_urbaine": "38",
      "taille_unite_urbaine": "7",
      "numero_unite_urbaine": "38701",
      "etablissement_public_cooperation_intercommunale": "200040715",
      "tranche_commune_detaillee": "43",
      "zone_emploi": "8210",
      "is_siege": "1",
      "enseigne": null,
      "indicateur_champ_publipostage": "A",
      "statut_prospection": null,
      "date_introduction_base_diffusion": "201508",
      "nature_entrepreneur_individuel": null,
      "libelle_nature_entrepreneur_individuel": null,
      "activite_principale": "9604Z",
      "libelle_activite_principale": "Entretien corporel",
      "date_validite_activite_principale": null,
      "tranche_effectif_salarie": null,
      "libelle_tranche_effectif_salarie": null,
      "tranche_effectif_salarie_centaine_pret": null,
      "date_validite_effectif_salarie": null,
      "origine_creation": null,
      "date_creation": "20150801",
      "date_debut_activite": "20150801",
      "nature_activite": null,
      "lieu_activite": null,
      "type_magasin": null,
      "is_saisonnier": null,
      "modalite_activite_principale": null,
      "caractere_productif": null,
      "participation_particuliere_production": null,
      "caractere_auxiliaire": null,
      "nom_raison_sociale": "SALUTE*PETELAZ-SALUTE/EMILIE/",
      "sigle": null,
      "nom": "SALUTE",
      "prenom": "EMILIE",
      "civilite": "MADAME",
      "numero_rna": null,
      "nic_siege": "00014",
      "region_siege": "84",
      "departement_commune_siege": "38421",
      "email": null,
      "nature_juridique_entreprise": "1000",
      "libelle_nature_juridique_entreprise": "Entrepreneur individuel",
      "activite_principale_entreprise": "9604Z",
      "libelle_activite_principale_entreprise": "Entretien corporel",
      "date_validite_activite_principale_entreprise": null,
      "activite_principale_registre_metier": null,
      "is_ess": null,
      "date_ess": null,
      "tranche_effectif_salarie_entreprise": null,
      "libelle_tranche_effectif_salarie_entreprise": null,
      "tranche_effectif_salarie_entreprise_centaine_pret": null,
      "date_validite_effectif_salarie_entreprise": null,
      "categorie_entreprise": "PME",
      "date_creation_entreprise": "201508",
      "date_introduction_base_diffusion_entreprise": "201508",
      "indice_monoactivite_entreprise": null,
      "modalite_activite_principale_entreprise": null,
      "caractere_productif_entreprise": null,
      "date_validite_rubrique_niveau_entreprise_esa": null,
      "tranche_chiffre_affaire_entreprise_esa": null,
      "activite_principale_entreprise_esa": null,
      "premiere_activite_secondaire_entreprise_esa": null,
      "deuxieme_activite_secondaire_entreprise_esa": null,
      "troisieme_activite_secondaire_entreprise_esa": null,
      "quatrieme_activite_secondaire_entreprise_esa": null,
      "nature_mise_a_jour": null,
      "indicateur_mise_a_jour_1": null,
      "indicateur_mise_a_jour_2": null,
      "indicateur_mise_a_jour_3": null,
      "date_mise_a_jour": "2016-07-18T14:38:50",
      "created_at": "2021-07-04T01:08:40.000+02:00",
      "updated_at": "2021-07-04T01:08:40.000+02:00",
      "longitude": "5.77163",
      "latitude": "45.179205",
      "geo_score": "0.97",
      "geo_type": "housenumber",
      "geo_adresse": "27 Avenue Jean Jaurès 38400 Saint-Martin-d'Hères",
      "geo_id": "38421_0470_00027",
      "geo_ligne": "G",
      "geo_l4": "27 AVENUE JEAN JAURES",
      "geo_l5": null
    }
  ],
  "spellcheck": null,
  "suggestions": [
    "salut les 60",
    "salut",
    "salut de la clarte",
    "salut l'artiste",
    "salut les copains",
    "salute",
    "salut les 60 coiffure",
    "salutem",
    "saluterre",
    "saluto"
  ]
}
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
