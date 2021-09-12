<template>
    <main class=" header">
      <v-container>
        <div class="display">
          <div class="nome">
              <h3>CALCULADORA</h3>
          </div>
          <div class="Resultado">
            <h3 class="result">{{resultadoCalc || '0'}}</h3><!--ARRUMAR O LAYOUT-->
          </div>
          <div class="Valores">
              <h2>{{ valorAparente || '0' }}</h2><!--REPASSA O VALOR QUE O valorAparente RECEBEU OU '0'-->
          </div>    
        </div > 
      </v-container>
            <v-app cols="12" >

                <div class="BotoesF1" cols="2">
                    <button class="bts"> MC </button>
                    <button class="bts"> MR </button>
                    <button class="bts"> M+ </button>
                    <button class="bts"> M- </button>
                    <button class="bts"> MS </button>
                    <button class="bts"> M </button>                  
                </div>

                <div class="BotoesF2" cols="3">
                    <button @click="porcento" class="btsF2"> % </button>
                    <button class="btsF2"> / </button>
                    <button @click="valorQuadrado" class="btsF2"> X² </button>
                    <button class="btsF2"> ¹/x </button>
                </div>

                <div class="BotoesInf">

                    <div class=" BotoesC1 " cols="3">
                        <button class="btsC1"> CE </button>
                        <button @click="deletarTudo" class="btsC1"> C </button> <!--//RESPONSÁVEL POR  DELETAR O VALOR TOTAL-->
                        <button @click="DeleteUm" class="btsC1"> DEL </button>
                        <button @click="divisao" class="btsC1"> / </button>
                    </div>

                    <div class="BotoesC2 " cols="3">
                        <button @click="numero('7')" class="btsC1"> 7 </button>
                        <button @click="numero('8')" class="btsC1"> 8 </button>
                        <button @click="numero('9')" class="btsC1"> 9 </button>
                        <button @click="multiplicar" class="btsC1"> X </button>
                    </div>

                    <div class=" BotoesC3 " cols="3">
                        <button @click="numero('4')" class="btsC1"> 4 </button>
                        <button @click="numero('5')" class="btsC1"> 5 </button>
                        <button @click="numero('6')" class="btsC1"> 6 </button>
                        <button @click="subtrair " class="btsC1"> - </button>
                    </div>
                    
                    <div class=" BotoesC4 " cols="3">
                        <button @click="numero('1')" class="btsC1"> 1 </button>
                        <button @click="numero('2')" class="btsC1"> 2 </button>
                        <button @click="numero('3')" class="btsC1"> 3 </button>
                        <button @click="adicao" class="btsC1"> + </button>
                    </div>
                    <div class=" BotoesC5 " cols="3">
                        <button @click="maisMenos" class="btsC1"> +- </button>
                        <button @click="numero('0')" class="btsC1"> 0 </button>
                        <button @click="virgula" class="btsC1"> , </button>
                        <button @click="Calc" class="btsC1"> = </button>
                    </div>

                </div>
            </v-app>  
    </main>
</template>
<script>

    export default {
        data(){
          return{

            resultadoCalc: '',
            valorAparente : '', 
            ultimoNumero: null,
            operador: null,
            clickOperador: false 

          };
        },

        methods:{

/*------------------------=>=>=>=>=>=>=>=>=>=> DELETA OS VALORES <=<=<=<=<=<=<=<=<=<=<=<=<=<=----------------------------*/

            deletarTudo(){
              this.valorAparente = '';          
              this.resultadoCalc = '';       
            },

            DeleteUm(){
              this.valorAparente = this.valorAparente.substr( 0, this.valorAparente.length -1);
              this.valorAparente;
            },

/*------------------------=>=>=>=>=>=>=>=>=>=> OPERADOR +/- || % || NUMERO CLICADO || , <=<=<=<=<=<=<=<=<=<=<=<=<=<=----------------------------*/

            maisMenos(){
              this.valorAparente = this.valorAparente.charAt(0) === '-' 
              ? this.valorAparente.slice(1) : `-${this.valorAparente}`; 
            },

            porcento(){          
              if(this.valorAparente === ''){ 
                this.valorAparente = 0;
                //console.log('Valor zero'); 
              } else {
                this.valorAparente = `${parseFloat(this.valorAparente) / 100}`;
              }
             // console.log('PORCENTAGEM FUNCIONANDO!')
            },

            numero(valor){
                if(this.clickOperador){
                  this.valorAparente = ''; 
                  this.clickOperador = false; 
                }
                this.valorAparente =`${this.valorAparente}${valor}`;            
            },

            virgula(){
                if(this.valorAparente.indexOf(',') === -1 ){ 
                  this.numero(','); 
                }           
            },

/*------------------------=>=>=>=>=>=>=>=>=>=> UTILIZADO NOS OPERADORES <=<=<=<=<=<=<=<=<=<=<=<=<=<=----------------------------*/

            setValue(){
                this.ultimoNumero = this.valorAparente;
                this.clickOperador = true; 
            },

/*------------------------=>=>=>=>=>=>=>=>=>=> RETORNA O RESULTADO <=<=<=<=<=<=<=<=<=<=<=<=<=<=----------------------------*/

            Calc(){             
                  this.resultadoCalc = `${this.operador( 
                    parseFloat(this.ultimoNumero),
                    parseFloat(this.valorAparente), 
                )}`;
            },

/*------------------------=>=>=>=>=>=>=>=>=>=> OPERADORES <=<=<=<=<=<=<=<=<=<=<=<=<=<=----------------------------*/

            divisao(){
              if(this.valorAparente === ''){
                this.valorAparente = ''
                } else{
                  this.valorAparente.indexOf('/');
                  this.numero('/') 
                }
              this.operador = (value1, value2) => value1 / value2;
              this.setValue(); 
            },

            multiplicar(){
              if(this.valorAparente === ''){
                this.valorAparente = ''
                } else{
                  this.valorAparente.indexOf('x');
                  this.numero('x')
                }
               this.operador = (value1, value2) => value1 * value2;
               this.setValue();
            },

            subtrair(){
              if(this.valorAparente === ''){
                this.valorAparente = ''
                } else{
                  this.valorAparente.indexOf('-');
                  this.numero('-') 
                }
              this.operador = (value1, value2) => value1 - value2;
              this.setValue();
            },

            adicao(){
              if(this.valorAparente === ''){
                this.valorAparente = ''
                } else{
                  this.valorAparente.indexOf('+');
                  this.numero('+')
                }
              this.operador = (value1, value2) => value1 + value2;
              this.setValue();             
            },

            valorQuadrado(){
              this.resultadoCalc = `${parseFloat(this.valorAparente) * this.valorAparente}`;

              if(this.clickOperador){
                this.resultadoCalc = ''; 
                this.clickOperador = false; 
              }else{
                 this.resultadoCalc = this.resultadoCalc * this.resultadoCalc;
              }
            } 
        }
    }
/*------------------------=>=>=>=>=>=>=>=>=>=> CRIANDO FUNCIONALIDADES MS || MC || MR || M- || M+  <=<=<=<=<=<=<=<=<=<=<=<=<=<=----------------------------*/





</script>
<style>

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
  .display{
  height: 175px;
  width: 100%;
}
  .btsF2{
    margin:0px 10px 7px 20px;
  }
  .btsC1{
    margin:0px 10px 7px 20px;
  }
  .Valores{
      float: right;
      width: 100%;
      height: 50px; 
      margin-top: 80px;
      bottom:0;
      padding-bottom: 0;
    }
  h2{
      font-size: 25px;
      float: right;
    }
    .result{
      float: right;
    }
     h2{
      float: right;
      
    }
    .result{
      float: right;
    }
    .nome{
      background-color:  #e6dfdf ;
    }
/* ------------------------------CONFIGURAÇÃO do TABLET---------------------------------- */

    @media (min-width: 768px){
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
      /* ------------------------------CONFIGURA O DISPLAY----------------------------------- */
      .display{
        height: 200px;
        width: 100%;
      }
      .btsC1{
        margin: 0px 30px 13px 14px;
      }
      .btsF2{
       margin:0px 20px 2px 30px;
      }
      .Valores{
        float: right;
        width: 100%;
        height: 50px; 
        margin-top: 80px;
        bottom:0;
        padding-bottom: 0;
    }
      h2{
        font-size: 25px;
        float: right;
    }
    .result{
      float: right;
    }
    .Resultado{
      font-size: 25px;
      width: 100%;
      height: 50px; 
    }
     h2{
      float: right;
      
    }
    .result{
      float: right;
    }
    .nome{
      background-color:  #e6dfdf ;
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
    /* ------------------------------CONFIGURA O DISPLAY----------------------------------- */
    .display{
      height: 200px;
      width: 100%;
    }
    .bts{
         margin:0px 15px 2px 25px;
      }
      .btsF2{
        margin:12px 40px 2px 35px ;
      }
    .btsC1{
      margin: 20px 40px 2px 35px ;
    }
    .Valores{
      float: right;
      width: 100%;
      height: 50px; 
      margin-top: 60px;
      bottom:0;
      padding-bottom: 0;
    }
    h2{
      float: right;
      
    }
    .result{
      float: right;
    }
    .nome{
      background-color:  #e6dfdf ;
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
}
</style>