<template>
  <div id="app">
    <b-container>
      <HeaderMasthead />
      <MovieCollection />
    </b-container>
  </div>
</template>

<script>
import HeaderMasthead from "./components/HeaderMasthead.vue";
import MovieCollection from "./components/MovieCollection.vue";

export default {
  name: "App",
  components: {
    HeaderMasthead,
    MovieCollection
  },
};
</script>

<style lang="scss"></style>
