<template>
    <main class=" header">
        <div class="display">
           <div>Ola Mundo</div>
        </div > 
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
                <div class="BotoesInf">
                    <div class=" BotoesC1 " cols="3">
                      <button> X² </button>
                      <button> X³ </button>
                      <button> sin </button>
                      <button> cos </button>
                    </div>
                    <div class="BotoesC2 " cols="3">
                      <button> X² </button>
                      <button> X³ </button>
                      <button> sin </button>
                      <button> cos </button>
                    </div>
                    <div class=" BotoesC3 " cols="3">
                      <button> X² </button>
                      <button> X³ </button>
                      <button> sin </button>
                      <button> cos </button>
                    </div>
                    <div class=" BotoesC4 " cols="3">
                      <button> X² </button>
                      <button> X³ </button>
                      <button> sin </button>
                      <button> cos </button>
                    </div>
                    <div class=" BotoesC5 " cols="3">
                      <button> X² </button>
                      <button> X³ </button>
                      <button> sin </button>
                      <button> cos </button>
                    </div>
                </div>
            </v-app>  

    </main>
</template>
<script>
export default {
    
}
</script>
<style>
  


/* ------------------------------CONFIGURA O DISPLAY----------------------------------- */
.display{
  height: 200px;
  width: 100%;
}

  /* ------------------------------CONFIGURAÇÃO do TABLET---------------------------------- */

 @media (min-width: 768px){
    button {
      margin: 15px;
      width:50px;
 
  }
  }
    /* ------------------------------CONFIGURAÇÃO do MOBILE---------------------------------- */

  @media (min-width: 320px){
    button {
      margin: 3px;
      width: 50px;
      height: 53px;
  }
  }

  @media (min-width: 320px){
  .header{
     position: fixed;
  }
  }
  /* ------------------------------CONFIGURAÇÃO do DESKTOP---------------------------------- */
   @media (min-width: 1024px){
    button {
      margin: 10px;
      width:auto;
      height: 37px;
    }
    .header{
     position: fixed;
  }
  /* ------------------------------CONFIGURAÇÃO DO HEADER ----------------------------------- */
    .header{
      margin-left:  35%;
      width: 30%;
      background-color: #f5f0f0;
    }
  }

/*----------------------------------BOTÕES DA CALCULADORA FILEIRAS 1 E 2---------------------------------------- */

.BotoesF1{
  background-color:  #f5f0f0;
  border-bottom: 2px solid #e6dfdf;
}
.BotoesF2{
  background-color:  #f5f0f0 ;
}
/*----------------------------------BOTÕES DA CALCULADORA COLUNAS 1 ATÉ 5---------------------------------------- */
.BotoesC1{
  background-color:  #e6dfdf ;
}
.BotoesC2{
  background-color:  #e6dfdf ;
}
.BotoesC3{
  background-color:  #e6dfdf ;
}
.BotoesC4{
  background-color:  #e6dfdf ;
}
.BotoesC5{
  background-color:  #e6dfdf ;
}

</style>