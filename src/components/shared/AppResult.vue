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
    max-height:100px;
    margin-right: 40px;
    position: relative;
}
     .estilBTN{
    max-width: 20%;
    max-height:100px;
    margin-right: 40px;
    position: relative;
  }
 }

/*=========================================>> CONFIG. TABLET <<=========================================== */


 @media (min-width: 768px){
   .estilBTN{
  height:60px;
  max-width: 15%;
  margin-left: 32%;
  margin-right: 40px;
  position: relative;
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
      color: brown !important;
      margin: 0px
    }
    .posicaoBTN{
      margin: 0;
      margin-left: 33.1%;
      margin-right: 65%;
      position: relative;
    }
 
}

</style>