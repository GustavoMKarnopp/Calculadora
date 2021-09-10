<template>
      <v-col class="text-center" cols="12">
       <AppLayout class="Layout"/>
      </v-col>
      <!--
         <v-col cols="6">
        <AppResult/>
      </v-col>
      -->
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
.Layout{
  height: 200px;
  margin-bottom: 0;
}

</style>
