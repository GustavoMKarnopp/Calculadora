<template>
    <v-sheet
      class=" overflow-hidden" 
      
    >

    <AppLayout class="Layout"/>

      <v-container >
        <v-row
        
        class="posicaoBTN"
        >
          <v-btn
            
            class="estilBTN"
            color="dark"
            dark
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

 @media (min-width: 320px){
  .posicaoBTN{
  max-width: 20%;
  max-height:100px;
  
  margin-right: 40px;
  position: relative;
}
 }

 @media (min-width: 768px){
   .posicaoBTN{
  height:60px;
  max-width: 20%;
  margin-left: 32%;
  margin-right: 40px;
  position: relative;
}
 }
  @media (min-width: 1024px){
  .posicaoBTN{
  height:60px;
  max-width: 20%;
  margin-left: 32%;
  margin-right: 40px;
  position: relative;
}
}

</style>