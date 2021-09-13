<template>
<div id="app">
  <v-app id="inspire">
    <v-sheet
      height="400"
      class="overflow-hidden"
      style="position: relative;"
    >
      <v-container class="fill-height">
        <v-row
          align="center"
          justify="center"
        >
          <v-btn
            color="black"
            dark
            @click.stop="drawer = !drawer"
          >
            Memory | History
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
            <v-list-item-title>Memory | History</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
  
        <v-divider></v-divider> <!--SERVE PARA DIVIDIR A TELA-->
  
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
  </v-app>
</div>
</template>
<script>
export default {
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
</style>