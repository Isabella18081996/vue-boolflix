<template>

<!-- creo un contenitore carta per il front e per il back -->
    <section class="carta">
      <div class="poster">
<!-- richiamo la foto corrispondente per metterla come copertina -->
        <img class="img-poster" v-if="card.poster_path !== null" :src="'https://image.tmdb.org/t/p/w342/'+card.poster_path" :alt="card.overview">

<!-- lato della carta da mostrare nel caso non ci dovesse essere un'immagine di copertina disponibile  -->
      <div class="not-found" v-if="card.poster_path === null">
        <div class="testi">
          <h4><span>Titolo: </span>{{card.title || card.name}}</h4>
          <h3>Cover not available</h3>
        </div>
        
      </div>
        
<!-- sezione per le informazioni del film/serie tv -->
      <div class="info draw">
        <ul >
          <li><span>Titolo: </span>{{ card.title || card.name}}</li>
          <li><span>Titolo originale: </span>{{ card.original_title  || card.original_name}}</li>

          <li v-if="flags.includes(card.original_language)">
            <span>Lingua: </span>
            <!-- passo l'immagine corrisponente al flag con la bandiera giusta -->
            <img :src="require(`@/assets/img/${card.original_language}.png`)" :alt="card.original_language">
          </li>
          <!-- se non ho la bandiera tra le mie immagini, allora viene mostrato solo il nome della lingua -->
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

<!-- creo due contenitori, uno per le stelle piene e uno per le stelle vuote -->
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

<!-- il contenitore delle stelle piene ha la larghezza/10* il voto delle stelle. In questo modo potrò avere le stelle mezze, 1/3 ecc -->
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

<!-- creo il mio paragrafo con la descrizione -->
          <div class="paragrafo"><p><span>Descrizione: </span><br>{{card.overview}}</p></div>
<!-- se non è presente nessuna descrizione nell'API -->
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
      /* creo delle flag da richiamare poi per mettere le immagini corrispondenti */
      flags:['en', 'it', 'es','fr','pt','de','ja'],
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

/* .star{
  color: white;
} */


  




</style>