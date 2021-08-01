<template>
  <v-app-bar app flat class="navbar">
    <div class="d-flex align-center">
      <p>Logo</p>
    </div>

    <v-spacer></v-spacer>
    <v-spacer></v-spacer>

    <div class="d-flex">
      <h4
        class="px-8 labels"
        v-for="(label, i) in ['Business Manager', 'MarketPlace', 'XooCam']"
        :key="i"
      >
        {{ label }}
      </h4>
    </div>
    <v-spacer></v-spacer>
    <div class="d-flex align-center">
      <h4 style="color:#E39400">Join Peexoo</h4>
      <v-icon>mdi-menu-down</v-icon>
    </div>
  </v-app-bar>
</template>

<script>
export default {
  name: 'Navbar',
};
</script>

<style lang="scss" scoped>
@import '../styles/variables.scss';

.navbar {
  box-shadow: 0px 1px 3px #00000029 !important;
  background-color: white !important;
}
.labels {
  font-size: 16px/25px;
  color: $almost-black;
  font-weight: 400;
}
</style>
