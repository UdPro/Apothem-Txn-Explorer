<template>
  <v-app>
    <v-main>
      <scanner/>
    </v-main>
  </v-app>
</template>

<script>
import scanner from './components/scanner';

export default {
  name: 'App',

  components: {
    scanner,
  },

  data: () => ({
    //
  }),
};
</script>
