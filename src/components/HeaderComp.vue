

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



    <div class="box-search col-2 offset-6 ">
      <input 
        v-model.trim="textToSearch"
        placeholder="Cerca..."
        class="form-control"
        type="text" />

      <div class="icon-holder">
        <div class="icon" id="video" @click="$emit('startSearch' , {text:textToSearch, type:'movie'})">
        <i class="fas fa-video"></i>
        <div class="tooltip">FILM</div>

      </div>
      <div class="icon" id="tv" @click="$emit('startSearch' , {text:textToSearch, type:'tv'})">
        <i class="fas fa-tv"></i>
        <div class="tooltip">SERIE TV</div>

      
      </div>
      <div class="icon" id="all" @click="$emit('startSearch' , {text:textToSearch, type:'all'})">
        <span> ALL</span>
        <!-- <i class="fas fa-tv"></i> -->
        <div class="tooltip">ALL</div>

      
      </div>
    </div>
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
@import '@/assets/styles/headerEffectTitle.scss';
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
   position: relative;
   margin-top:50px;

input{
  position: relative;
  border: 2px solid red;
  height: 40px;
  background: transparent;
  width: 200px;
  border-radius: 50px;
  padding-left: 20px;
  padding-right: 20px;
  padding-top: 4px;
  padding-bottom: 4px;
  font-size: 15px;
  color: gray; 
}
input:focus{
  outline: none;
}
  
    

.icon-holder{
display: flex;
margin:10px 10px;
}


.icon{
  position: relative;
  height: 40px;
  width: 40px;
  background: red;
  border-radius: 100%;
  /* box-shadow: 0px 1px 2px; */
  cursor: pointer;
  opacity: 0;
  transition: .4s;
  display: flex;
  align-items: center;
  margin-left: 15px;
}
.icon:hover{
     background: white;
     color:red;
     animation-play-state: paused;  
     box-shadow: 0 0 30px rgba(209, 54, 54, 0.75);
}
 

.icon i{
  color: white;
  font-size: 18px;
  padding: 8px;
  /* text-align: center; */
 /*  transform: translate(50%,-50%); */
}
.icon:hover i{
  color: red;
}

/* #parking:after{
   content: '\f26c';
  font-weight: bold;
  position: absolute;
  font-size: 13px;
  color: white;
  background: red;
  padding: 1px 3px 1px 4px;
  border-radius: 100%;
  left: 10px;
  top: 9px;
} */


input:focus ~ .icon-holder > .icon{
  animation: ani 2.2s ease-out infinite
}
  
  @keyframes ani{
      0%{
       opacity: 1 
      }

      
    10%{
           transform: scale(1.2);
      opacity: 1
    }
 
    20%{
           transform: scale(1);
      opacity: 1
    }
 
    100%{
      transform: scale(1);
      opacity: 1 
    }
      
  }
 
  #tv{
    animation-delay: .3s;
    
  }
  
    
#all{
  animation-delay: .6s
}
  

.tooltip{
   opacity: 0;
  position: absolute;
  font-size: 12px;
  color: white;
  background: #555;
  padding: 8px;
  top: 30px;
  border-radius: 15%;
  top: 45px ;
}
.tooltip:after{
     content: '';
    position: absolute;
    background: #555;
    clip-path: polygon(70% 0%, 0% 100%, 100% 100%);
    height: 18px;
    width: 18px;
    top: -10px;
    left: 7px ;
}
  

  
.icon:hover > .tooltip{
  animation: ani .4s ease-out forwards;
  animation-delay: .3s ;
}

span{
  font-family: 'Squada One', cursive;
  color:white;
  font-weight: 700;
  text-align: center;
  padding-left: 5px;
  font-size: 20px;
}

span:hover{
  color: red;
}
}



}
 


</style>