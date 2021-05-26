<template>
  <section class="d-flex flex-wrap justify-content-center">
    <ul 
    v-for="(film, index) in films" :key="index"
    class="col-3 m-3">
      <li>Titolo <span>{{film.title}}</span></li>
      <li>Titolo originale: <span>{{film.original_title}}</span></li>
      <li>Lingua: <span>{{film.original_language}}</span></li>
      <li>Voto: <span>{{film.vote_average}}</span></li>
    </ul>
    
  </section>
</template>

<script>
export default {
 name:'SectionFilmComp',
 props:{
   films: Array,
 }
}
</script>

<style lang="scss" scoped>
 section{
   background-image: linear-gradient(#000000, #711414, #be1010);

   ul{
     color: #FFFFFF;
     border: 1px solid #FFFFFF;
      margin: 2px;
      &:hover{
          transform: scale(1.05, 1.05);
          filter:brightness(110%);
          box-shadow: 0 15px 15px rgba(0,0,0,.3);
        }
      
     li{
       font-size: 20px;
       padding-right: 10px;
       
     };
     span{
       font-size:15px;
       font-style: italic;
     }
   };
 };
</style>
