<template>
  <div id="app">

    <HeaderComp @startSearch="startSearch" />

    
    <!-- <h2 v-if="results.movie.length === 0 && results.tv.length === 0">Nessun risultato trovato</h2> -->


    <!-- LOGO IN MOVIMENTO -->
    <div class="deconstructed" v-if="results.movie.length === 0 && results.tv.length === 0">
        NESSUN RISULTATO TROVATO
      <div>NESSUN RISULTATO TROVATO</div>
      <div>NESSUN RISULTATO TROVATO</div>
      <div>NESSUN RISULTATO TROVATO</div>
      <div>NESSUN RISULTATO TROVATO</div>
    </div>

    
    <MainComp v-if="results.movie.length > 0"  type='movie' :list="results.movie" />
    <MainComp v-if="results.tv.length > 0" type='tv' :list="results.tv"/>

    <LoaderComp title="Attendi" v-else/>

  </div>
</template>

<script>
/* importo i vari componenti */
import HeaderComp from './components/HeaderComp';
import MainComp from './components/MainComp';
import LoaderComp from './components/MainComp';

import axios from 'axios';
export default {
  name: 'App',
  components: {
    HeaderComp,
    MainComp,
    LoaderComp
  },
  /* Richiamo l'API esterno e definisco cosa mi deve mostrare */
  data(){
    return{
      apiUrl: 'https://api.themoviedb.org/3/search/',
      apiKey: 'e9c3e699c20e864258f32138e6f6d820',
      results:{
        'movie':[],
        'tv':[]
      }
    }
  },
  /* creo la funzione per fare la ricerca nell'input di movie, serie tv e tutto */
  methods:{
    startSearch(obj){
      this.resetResults();
      if(obj.type === 'all'){
        this.getAPI(obj.text, 'movie');
        this.getAPI(obj.text, 'tv');
      }else{
        this.getAPI(obj.text, obj.type);
      }
    },
    resetResults(){
      this.results.movie = [];
      this.results.tv = [];
    },
    getAPI(query, type){
      
      if(query !== ''){
        axios.get(this.apiUrl+type,{
            params:{
              api_key: this.apiKey,
              query: query,
              language: 'it-IT'
            }
          })
          .then(res => {
            this.results[type] = res.data.results;
            console.log('MOVIE',this.results.movie);
            console.log('TV', this.results.tv);
          })
          
          .catch(err => {
            console.log(err);
          })
          
      }
    }
  },

  /* Creo nella schermata iniziale la lista dei film più popolari per evitare che ci sia lo spazio vuoto dato dagli array vuoti di movie e serie tv */
  created(){
    
      let type = 'movie'
      axios.get('https://api.themoviedb.org/3/movie/popular',{
          params:{
            api_key: this.apiKey,
            language: 'it-IT'
          }
        })
        .then(res => {
           this.results[type] = res.data.results;
        })
        .catch(err => {
          console.log(err);
        })
    
  }
}

</script>

<style lang="scss">
/* importo i file scss generale e del testo che appare quando gli array sono vuoti */
@import './assets/styles/general';
@import './assets/styles/scrollText.scss';



/* h2{
  text-align: center;
  padding-top: 20px;
} */

</style>
