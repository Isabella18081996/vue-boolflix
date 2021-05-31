<template>

    <section class="carta">
      <div class="poster">
        <!-- <img class="img-poster" :src=" 'http://image.tmdb.org/t/p/w342' + card.poster_path " :alt='card.overwiev'>  -->

        <img class="img-poster" v-if="card.poster_path !== null" :src="'https://image.tmdb.org/t/p/w342/'+card.poster_path" :alt="card.overview">

      <div class="not-found" v-if="card.poster_path === null">
        <div class="testi">
          <h4><span>Titolo: </span>{{card.title || card.name}}</h4>
          <h3>Not found cover</h3>
        </div>
        
      </div>
        

      <div class="info draw">
        <ul >
          <li><span>Titolo: </span>{{ card.title || card.name}}</li>
          <li><span>Titolo originale: </span>{{ card.original_title  || card.original_name}}</li>

          <li v-if="flags.includes(card.original_language)">
            <span>Lingua: </span>
            <img :src="require(`@/assets/img/${card.original_language}.png`)" :alt="card.original_language">
          </li>
          <li v-else><span>Lingua: </span>{{ card.original_language }}</li>


<!--           <div class="stars"
            v-for="index in 5" :key="index">
            <i class=" fas fa-star"
               v-if="index < Math.round(card.vote_average/2)"></i>
            <i 
              class=" star far fa-star"
                v-else></i>
              </div> -->
          <!-- <li><span>Voto: <i class="fas fa-star"></i></span>{{ card.vote_average }}</li> -->
          <div>
            <span><strong>Voto: </strong></span>

            <div class="stars">

              <div class="empty">
                <ul class="inner stelle">
                  <li><i class="far fa-star"></i></li>
                  <li><i class="far fa-star"></i></li>
                  <li><i class="far fa-star"></i></li>
                  <li><i class="far fa-star"></i></li>
                  <li><i class="far fa-star"></i></li>


                </ul>
              </div>

              <div class="solid" :style="`width:${19.9*card.vote_average}px`">
                <ul class="inner stelle">
                  <li><i class="fas fa-star"></i></li>
                  <li><i class="fas fa-star"></i></li>
                  <li><i class="fas fa-star"></i></li>
                  <li><i class="fas fa-star"></i></li>
                  <li><i class="fas fa-star"></i></li>


                </ul>
              </div>
              
            </div>

          </div>

          <div class="paragrafo"><p><span>Descrizione: </span><br>{{card.overview}}</p></div>
          <li v-if="card.overview === ''">
          <h6>Nessuna descrizione trovata</h6>
        </li>
          

          

       </ul>
      </div>
      </div>

       
    </section>
</template>

<script>
export default {
  name: 'Card',
  props:{
    card:Object,
  },
  data(){
    return{
      flags:['en', 'it', 'es','fr','pt','de','ja'],
 /*      imgs:{
        'en': 'en',
        'it' : 'it',
        'es' : 'es',
        'fr' : 'fr',
        'pt' : 'pt',
        'de' : 'de',
        'ja' : 'ja'


      } */
    }
  },
  
}
</script>

<style lang='scss'>
@import '@/assets/styles/cardEffect.scss';
/* .stars{
  display: inline-block;
  color: #ff0;
  text-shadow: 0 0 40px #ffc;
  text-shadow: #fc0 0 0 20px;
  margin-top: 20px;
  padding: 5px;
} */
.star{
  color: white;
}


  


  .stars{
  position:relative;
  width: 200px;
  height: 25px;
  line-height: 55px;
  margin-bottom: 15px;

  .empty, .solid{
    position:absolute;
    top: -70px;
    left: 60px;
    overflow: hidden;
    border-radius: 20px; 
  

 

  }
  .inner{
    width: 199px;
  }

  .stelle{
 /*     color: #FFFFFF;
 list-style: none;
 padding-top:30px ;
 margin-left: -15px; */
 margin-bottom: 15px;
  }
  li{
    display: inline;   
    
  }
  i{
    font-size: 20px;
    text-align: center;
    padding-left: 5px;
    padding-right: 5px;

       color: #ff0;
  

  }
  .solid li i{
  text-shadow: rgb(236, 220, 127) 0 0 25px;
  /* padding-right: 5px ; */
/*       padding-left: 5px;
    margin-right: 5px; */


  }

  .paragrafo .description{
       font-size:5px;
   color: white;
   font-weight: 500;
  }
  }


</style>