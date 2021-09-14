<template>
<main class="body">
    <v-sheet
      class=" overflow-hidden" 
    >

    <AppLayout class="Layout"/>

      <v-container >
        <v-row
        class="posicaoBTN"
        >
          <v-btn 
            @click.stop="drawer = !drawer"
          >
            Hist
          </v-btn>
        </v-row>
      </v-container>
  
      <v-navigation-drawer
        v-model="drawer"
        absolute
        temporary
      >
        <v-list-item>  
          <v-list-item-content>
            <v-list-item-title>History | Memeory</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
  
        <v-divider></v-divider>
  
        <v-list dense>
          <v-list-item
            v-for="item in items"
            :key="item.title"
            link
          >
          <v-list-item-content>
            <v-list-item-title>{{ item.title }}</v-list-item-title>
          </v-list-item-content>
          </v-list-item>
        </v-list>
      </v-navigation-drawer>
    </v-sheet>
  </main>
</template>
<script>
  import AppLayout from './AppLayout.vue'
export default {
  components:{
    AppLayout,
  },
    data () {
     
    return {
      drawer: null,
      items: [
        { title: 'Memory' },
        { title: 'History' },
      ],
    }
  },
}

</script>
<style>

/*=========================================>> CONFIG. MOBILE <<=========================================== */

 @media (min-width: 320px){
   .posicaoBTN{
    max-width: 20%;
    max-height: 100px;
    margin-right: 40px;
    float: right;
    margin: 0;
    position: relative;
  }
    .v-btn{
    max-height: 32px !important;
    color: #e6dfdf !important;
    margin: -2px -6px 0px 0px;
  }
  .v-btn span{
    font-size: 13px;
    color: rgb(14, 11, 11) !important;
  }
  .theme--light.v-btn.v-btn--has-bg {
    background-color:  #cfcdcd !important;
    color: darkblue !important;
  }
 }

/*=========================================>> CONFIG. TABLET <<=========================================== */


 @media (min-width: 768px){
    .v-btn{
    max-height: 30px !important;
    color:   #e6dfdf  !important;
    margin: 0px
  }
  .v-btn span{
   font-size: 13px;
    color: rgb(14, 11, 11) !important;
  }
  .theme--light.v-btn.v-btn--has-bg {
      background-color:  #cfcdcdb9 !important;
      color: darkblue !important;
  }
    .posicaoBTN{
    height:60px;
    max-width: 20%;
    max-height: 20%;
    margin-left: 32%;
    margin-right: 40px;
    position: relative;
  }
}

/*=========================================>> CONFIG. DESKTOP <<=========================================== */


@media (min-width: 1024px){  
  .v-btn{
    max-height: 30px !important;
    color:#e6dfdf  !important;
    margin: 0px
  }
  .v-btn span{
   font-size: 13px;
    color: rgb(14, 11, 11) !important;
  }
.theme--light.v-btn.v-btn--has-bg {
    background-color:  #cfcdcdb9 !important;
    color: darkblue !important;
}
  
.posicaoBTN{
  margin: 0;
  margin-left: 33.1%;
      margin-right: 61%;
  position: relative;
}
 
}

</style>