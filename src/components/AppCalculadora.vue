<template>
  <v-container>
    <v-row class="text-center">
      <v-col cols="12">
       <AppLayout/>
      </v-col>
      <!--
         <v-col cols="6">
        <AppResult/>
      </v-col>
      -->
    </v-row>
  </v-container>
</template>

<script>
import AppLayout from './shared/AppLayout.vue'
//import AppResult from './shared/AppResult.vue'
  export default {
    name: 'AppCalculadora',

    data: () => ({
     
    }),
    components:{
      AppLayout,
    //  AppResult
    }
  }
</script>
<style>


</style>
