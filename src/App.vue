<template>
  <v-app>
    <v-app-bar
      app
      color="dark"
      dark
    >
      <h1> Lista de Universidades alrededor del mundo </h1>
    </v-app-bar>

    <v-main>
      <universities/>
    </v-main>
  </v-app>
</template>

<script>
import universities from './components/universities';

export default {
  name: 'App',

  components: {
    universities
  },

  data: () => ({
    //
  }),
};
</script>
