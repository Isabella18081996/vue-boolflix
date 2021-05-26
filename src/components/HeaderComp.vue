<template>
  <header class="d-flex align-items-center">
    <div class="logo col-3 offset-1">
      <h1>boolflix</h1>
    </div>

    <div class="box-search col-3 offset-4 d-flex justify-content-evenly">
      <input
      @click="resetSearch"
      @keyup="startSearch"
      v-model.trim="strFilm" 
      type="text" placeholder="Cerca...">
      <button
      @click="filmFunctionSearch" 
      class="btn btn-outline-danger"><i class="fas fa-search"></i></button>
    </div>
  </header>
</template>

<script>
export default {
 name:'HeaderComp',
 props:{
   filmFunctionSearch: Function,
 },
 data(){
   return{
     strFilm:'',
   }
 },
 methods:{
    startSearch(){
      this.$emit('searchingFilms', this.strFilm);
    },
    resetSearch(){
      this.strFilm='';
      this.startSearch();
    }
 }
}
</script>

<style lang="scss" scoped>
header{
  background-color:#000000;
  height: 80px;
  .logo{
    h1{
      color: #EC0000;
      text-transform: uppercase;
      margin:0;
    };
  };
  .box-search{
    input{
     width: 300px;
     padding-left: 10px;
     color:white;
     outline: none;
     background-color:transparent;
     border: 1px solid darkgrey;
     border-radius: 5px;

      &:hover{
        border: 1px solid #EC0000;
      };
    };
  };
}
</style>


