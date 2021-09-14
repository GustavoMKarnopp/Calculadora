<template>
      <v-col class="text-center" cols="12">
       <AppResult/>
       <AppLayout class="Layout"/>
      </v-col>
</template>

<script>
import AppLayout from './shared/AppLayout.vue'
import AppResult from './shared/AppResult.vue'
  export default {
    name: 'AppCalculadora',

    data: () => ({
     
    }),
    components:{
      AppLayout,
      AppResult
    }
  }
</script>
<style>

</style>
