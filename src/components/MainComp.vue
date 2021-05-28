<template>
  
  <main>
    <h1>{{ titles[type] }}</h1>
    <section class="d-flex flex-wrap justify-content-center">
      <Card
      v-for="card in list"
      :key="card.id"
      :card="card"
     /> 
    </section>
  </main>
</template>

<script>
import Card from '@/components/Card';
export default {
  name: 'Main',
  components:{
    Card
  },
  props:{
    type: String,
    list: Array
  },
  data(){
    return{
      titles:{
        'movie': 'Film trovati nel nostro catalogo',
        'tv': 'Serie tv trovate nel nostro catalogo'
      }
    }
  }
}
</script>

<style lang="scss" scoped>
main{
  background-color:black;
}
h1{
  text-align: center;
  padding: 20px;
  font-weight: 600;
}
</style>