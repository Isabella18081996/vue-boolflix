<template>
  <div id="app">

    <HeaderComp @startSearch="startSearch" />

    <h2 v-if="results.movie.length === 0 && results.tv.length === 0">Nessun risultato trovato</h2>
<!--     <div class="notfound deconstructed" v-if="results.movie.length === 0 && results.tv.length === 0">
        NESSUN RISULTATO TROVATO
      <div>NESSUN RISULTATO TROVATO</div>
      <div>NESSUN RISULTATO TROVATO</div>
      <div>NESSUN RISULTATO TROVATO</div>
      <div>NESSUN RISULTATO TROVATO</div>
    </div> -->

    <MainComp v-if="results.movie.length > 0"  type='movie' :list="results.movie" />
    <MainComp v-if="results.tv.length > 0" type='tv' :list="results.tv"/>

    <LoaderComp title="Attendi" v-else/>

  </div>
</template>

<script>
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
  data(){
    return{
      apiUrl: 'https://api.themoviedb.org/3/search/',
      apiKey: 'e9c3e699c20e864258f32138e6f6d820',
      loading:true,
      results:{
        'movie':[],
        'tv':[]
      }
    }
  },
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
  created(){}
}
</script>

<style lang="scss">
@import './assets/styles/general';
/* @import './assets/styles/mixin.scss';
.notfound{
  @include messaggio();
} */
h2{
  text-align: center;
  padding-top: 20px;
}

</style>
