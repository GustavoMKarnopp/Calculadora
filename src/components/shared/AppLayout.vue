<template>
    <main class="header">
        <div class="display">
           <div>Ola Mundo</div>
        </div> 
            <v-app cols="12" >
                <div class="BotoesF1" cols="2">
                 <button> MC </button>
                  <button> MB </button>
                  <button> M+ </button>
                  <button> M- </button>
                  <button> MS</button>
                  <button> M</button>
                  
                </div>
                <div class="BotoesF2" cols="3">
                  <button> X² </button>
                  <button> X³ </button>
                  <button> sin </button>
                  <button> cos </button>
                </div>
            </v-app>  

    </main>
</template>
<script>
export default {
    
}
</script>
<style>
main{
  margin: 0;
  padding: 0;
  background-color: #e6dfdf;

}
.display{
  height: 200px;
  width: 100%;
}


 @media (min-width: 768px){
    button {
      height: 30px;
      margin: 15px;
      width:50px;
      
  }
  }
  @media (min-width: 320px){
    button {
      
      margin: 3px;
      width: 50px;
      
  }
  }
   @media (min-width: 1024px){
    button {
      height: 10px;
      margin: 35px;
      width:50px;
      
  }
  }
/*----------------------------------BOTÕES DA CALCULADORA---------------------------------------- */

.BotoesF1{
  background-color:  #e6dfdf;
  border-bottom: 2px solid #838282;
}
.BotoesF2{
  background-color:  #e6dfdf ;
  border-bottom: 2px solid #838282;
}

</style>