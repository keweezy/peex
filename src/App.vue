<template>
  <v-app>
    <Navbar />

    <v-main>
      <MainPage />
    </v-main>
  </v-app>
</template>

<script>
// import HelloWorld from './components/HelloWorld';
import Navbar from './components/Navbar.vue';
import MainPage from './views/MainPage.vue';

export default {
  name: 'App',

  components: {
    // HelloWorld,
    Navbar,
    MainPage,
  },

  data: () => ({
    //
  }),
};
</script>
