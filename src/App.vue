<template>
  <v-app>
    <v-main>
      <AppCalculadora/>
    </v-main>
  </v-app>
</template>

<script>
import AppCalculadora from './components/AppCalculadora';

export default {
  name: 'App',

  components: {
    AppCalculadora,
  },

  data: () => ({
    //
  }),
};
</script>
