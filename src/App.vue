<template>
  <div id="app">
    <HeaderComp
    :filmFunctionSearch="readArrFilm"
    @searchingFilms="generatorText"
    />

    <main>
      <SectionFilmComp
      :films="arrFilm"
      />
    </main>
  </div>
</template>

<script>
import axios from 'axios';
import HeaderComp from './components/HeaderComp.vue';
import SectionFilmComp from './components/SectionFilmComp.vue';
export default {
  name: 'App',
  components: {
    HeaderComp,
    SectionFilmComp
    
  },
  data(){
    return{
      apiURL:'https://api.themoviedb.org/3/search/movie',
      apiKey:'e9c3e699c20e864258f32138e6f6d820',
      query:'',
      arrFilm:[],
    }
  },
  methods:{
    
    readArrFilm(){
      console.log(this.query);
      axios.get(this.apiURL,{
        params:{
          api_key: this.apiKey,
          query: this.query,
          language:'it-IT',
        },
      })
      .then(resp => {
        console.log(resp.data.results);
        this.arrFilm = resp.data.results;
        console.log(this.arrFilm);
      })
      .catch(err =>{
        console.log(err);
      })
      
    },
    generatorText(text){
      this.query = text;
      console.log(this.query);
    }
  }
}
</script>

<style lang="scss">
@import '@/assets/styles/general.scss';
</style>
