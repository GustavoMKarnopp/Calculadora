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
          <div maxlength="10" class="Valores">
              <h2  class="valorTela" v-show="!valQuadrado">{{ valorAparente || '0' }}</h2><!--REPASSA O VALOR QUE O valorAparente RECEBEU OU '0'-->
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
                    <button @click="raiz" class="btsF2"> / </button>
                    <button @click="valorQuadrado" class="btsF2"> X² </button>
                    <button @click="xum" class="btsF2"> ¹/x </button>
                </div>

                <div class="BotoesInf">

                    <div class=" BotoesC1 " cols="3">
                        <button @click="deletarTudo" class="btsC1"> CE </button>
                        <button @click="deletar" class="btsC1"> C </button> <!--//RESPONSÁVEL POR  DELETAR O VALOR TOTAL-->
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
            clickOperador: false,
            valQuadrado: false
          };
        },

        methods:{
/*------------------------=>=>=>=>=>=>=>=>=>=> DELETA OS VALORES <=<=<=<=<=<=<=<=<=<=<=<=<=<=----------------------------*/

            deletar(){
              this.valQuadrado = false;
              this.valorAparente = '';          
              this.resultadoCalc = '';       
            },
            deletarTudo(){ 
              this.valQuadrado = false;          
                this.valorAparente = '';               
            },

            DeleteUm(){
              this.valQuadrado = false;
              this.valorAparente = this.valorAparente.substr( 0, this.valorAparente.length -1);
              this.valorAparente;
            },

/*------------------------=>=>=>=>=>=>=>=>=>=> OPERADOR +/- || % || NUMERO CLICADO || , <=<=<=<=<=<=<=<=<=<=<=<=<=<=----------------------------*/

            maisMenos(){
              this.valQuadrado = false;
              this.valorAparente = this.valorAparente.charAt(0) === '-' 
              ? this.valorAparente.slice(1) : `-${this.valorAparente}`; 
            },

            porcento(){  
              this.valQuadrado = false;        
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
                if(this.valorAparente === ''){
                    this.valorAparente = '0,'
                  } else if(this.valorAparente.indexOf(',') === -1 ){ 
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
             if(this.valorAparente === ''){ 
                 this.valorAparente = 0
                }else{
                   this.resultadoCalc = `${this.operador( 
                    parseFloat(this.ultimoNumero),
                    parseFloat(this.valorAparente), 
                )}`;
                }
            },

/*------------------------=>=>=>=>=>=>=>=>=>=> OPERADORES <=<=<=<=<=<=<=<=<=<=<=<=<=<=----------------------------*/

            divisao(){
              this.valQuadrado = false;
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
              this.valQuadrado = false;
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
              this.valQuadrado = false;
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
              this.valQuadrado = false;
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
                this.valQuadrado = true;
                this.valorAparente = this.valorAparente * this.valorAparente;
                this.resultadoCalc = this.valorAparente;    
               
           },
           raiz(){
             this.valQuadrado = true;
              this.valorAparente = Math.sqrt(this.valorAparente);
              this.resultadoCalc = this.valorAparente;
          },

           xum(){
             this.valQuadrado = true;
             if(this.valorAparente === '' || this.valorAparente === '0'){
               this.resultadoCalc = this.valorAparente = 'Não é possível dividir por zero!'
             }else{
               this.valorAparente = 1/(this.valorAparente);
               this.resultadoCalc = this.valorAparente;
             }
          },
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
    margin: 0px 11px 7px 0px;
    height: 53px;
    width: 70px;
  }
  .btsC1{
    height: 53px;
    width: 70px;
    margin:0px 0px 7px 10px;
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
    white-space: nowrap; 
      text-align: right;
      width: 15em; 
      overflow: hidden;
      text-overflow: ellipsis; 
      font-size: 20px;
      float: right;
    }
    .result{
      opacity: 0.5;
      float: right;
    }
     h2{
      float: right;
      
    }
    .nome{
      background-color:  #e6dfdf ;
    }
/* ------------------------------CONFIGURAÇÃO do TABLET---------------------------------- */

    @media (min-width: 768px){
      button {
        margin: 8px;
        width: auto;
        height: 30px;
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
     .btsF2{
        margin: 5px 0px 5px 10px;
        height: 35px;
        width: 40px;
      }
    .btsC1{
        margin: 5px 4px 6px 7px;
        height: 40px;
        width: 43px;
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
      white-space: nowrap; 
      text-align: right;
      width: 10em; 
      overflow: hidden;
      text-overflow: ellipsis; 
      font-size: 14px;
      float: right;
    }
    .result{
      opacity: 0.5;
      float: right;
    }
    .Resultado{
      font-size: 20px;
      width: 100%;
      height: 50px; 
    }
     h2{
      white-space: nowrap; 
      text-align: right;
      width: 15em; 
      overflow: hidden;
      text-overflow: ellipsis; 
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
        margin: 0px 0px 0px 20px;
        height: 40px;
        width: 75px;
      }
    .btsC1{
        margin: 5px 0px 0px 10px;
        height: 54px;
        width: 85px;
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
      font-size: 20px;
      float: right;
    }
    .result{
      font-size: 25px;
      opacity: 0.5;
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