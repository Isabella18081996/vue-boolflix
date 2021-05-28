<template>
  <header class="d-flex align-items-center">

    <div class="logo col-3 offset-1">
      <div class="words word-1">
  <span>B</span>
  <span>O</span>
  <span>O</span>
  <span>L</span>
  <span>F</span>
  <span>L</span>
  <span>I</span>
  <span>X</span>

</div>
    </div>


    <div class="box-search col-2 offset-5 d-flex justify-content-evenly">
     
      <input 
        v-model.trim="textToSearch"
        placeholder="Cerca..."
        class="form-control"
        type="text" />

      <div class="icona"><i class="fas fa-search"></i></div>
      <select class="form-select">
        <option selected>scegli <i class="fas fa-search"></i></option>
        <option @click="$emit('startSearch' , {text:textToSearch, type:'movie'})">Film</option>
        <option @click="$emit('startSearch' , {text:textToSearch, type:'tv'})">Serie tv</option>
        <option @click="$emit('startSearch' , {text:textToSearch, type:'all'})">All</option>
      </select>

      

    </div>
    
  </header>
</template>

<script>
export default {
  name: 'Haed',
  data(){
    return{
      textToSearch: ''
    }
  }
}
</script>

<style lang="scss" scoped>
header{
  background-color:#000000;
  height: 80px;
  .logo{
   .words {
  color: red;
  font-size: 0;
  line-height: 1.5;
}

.words span {
  font-size: 40px;
  font-weight: 600;
  display: inline-block;
  animation: move 3s ease-in-out infinite;
}

@keyframes move {
  0% {
    transform: translate(-30%, 0);
  }
  50% {
    text-shadow: 0 25px 50px rgba(209, 54, 54, 0.75);
  }
  100% {
    transform: translate(30%, 0);
  }
}

.words span:nth-child(2) {
  animation-delay: 0.1s;
}

.words span:nth-child(3) {
  animation-delay: 0.2s;
}

.words span:nth-child(4) {
  animation-delay: 0.3s;
}

.words span:nth-child(5) {
  animation-delay: 0.4s;
}

.words span:nth-child(6) {
  animation-delay: 0.5s;
}

.words span:nth-child(7) {
  animation-delay: 0.6s;
}

.words span:nth-child(8) {
  animation-delay: 0.7s;
}

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
    .icona{
      display: flex;
      align-items: center;
      margin-left:30px;
      margin-right:10px;

    }
    select{
      width: 120px;
      color:red;
      background-color:transparent;
      border: 3px solid red
      option{
        background-color: transparent;
      }
    }
  };
}
</style>


