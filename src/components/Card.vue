<template>

    <section class="carta">
      <div class="poster">
        <img class="img-poster" :src=" 'http://image.tmdb.org/t/p/w342' + card.poster_path " :alt='card.overwiev'>
      <div class="info">
        <ul >
          <li><span>Titolo: </span>{{ card.title || card.name}}</li>
          <li><span>Titolo originale: </span>{{ card.original_title  || card.original_name}}</li>
          <li
            v-if="card.original_language !== 'en' && card.original_language !== 'it' && card.original_language !== 'es' && card.original_language !== 'fr' && card.original_language !== 'pt' && card.original_language !== 'de' && card.original_language !== 'ja'">
           <span>Lingua: </span> {{card.original_language}}
          </li>
          <li
            v-if="card.original_language === 'en' || card.original_language === 'it' || card.original_language === 'es' || card.original_language === 'fr' || card.original_language === 'pt' || card.original_language === 'de' || card.original_language === 'ja'">
            <span>Lingua: </span><img :src="require('../assets/img/flag-'+imgs[card.original_language]+'.png')" :alt="'flag-'+imgs[card.original_language]">
          </li>
          <li><span>Voto: <i class="fas fa-star"></i></span>{{ card.vote_average }}</li>

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
      imgs:{
        'en': 'en',
        'it' : 'it',
        'es' : 'es',
        'fr' : 'fr',
        'pt' : 'pt',
        'de' : 'de',
        'ja' : 'ja'


      }
    }
  }
}
</script>

<style lang='scss'>
  .carta{
      background-color: rgba(59, 46, 52, 0.2);
      cursor: pointer;
      position: relative;
      margin-right: 10px;
      margin-bottom: 10px;
      overflow: hidden;
      max-height: 500px;
    
      .poster .img-poster{
        width: 100%;
        transition: width 2s, height 2s, transform 4s;
      }
      &:hover .poster .img-poster{
        opacity: .05;
       transform:rotateY(180deg)scale(0.5,0.5)rotateY(180deg);
       
      }
      &:hover .info{
        position: absolute;
        top: 0;
        display: block;
        width: 100%;
      }
      &:hover .poster{
        background-color: rgba(172, 172, 240, 0.2);
      }
      .info{
        display: none;
        height: 100%;
        border: 2px solid white;
        color: white;
        padding: 5px;
      }
      ul{
     color: #FFFFFF;
     list-style: none;
     padding-top:30px ;
     li{
       font-size: 15px;
       padding-left:0px;      
       img{
         width: 35px;
       }
     };
     span{
       font-size:20px;
       color: white;
       font-weight: 600;
     }
    i{
      color: yellow;
      }
   };


      }
</style>