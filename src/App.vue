<template>
  <div id="app">
    <Header @search="getMovies" />
    <main>
      <Main />
      <ul v-for="(movie, index) in moviesList" :key="index">
        <li>{{ movie.title }}</li>
        <li>{{ movie.original_title }}</li>
        <li>{{ movie.original_language }}</li>
        <li>{{ movie.vote_average }}</li>
      </ul>
    </main>
  </div>
</template>

<script>
import axios from "axios";
import Header from "./components/Header.vue";
import Main from "./components/Main.vue";
export default {
  name: "App",
  components: {
    Header,
    Main,
  },
  data() {
    return {
      moviesList: [],
      api: {
        basaUri: "https://api.themoviedb.org/3/",
        key_api: "12dd05e7d86d7822ce2c8e30b16accee",
      },
    };
  },
  created() {},
  methods: {
    getMovies(query) {
      console.log("Search recuperato ", query, " nell'App");
      if (!query) this.moviesList = [];

      //*search/movie? da cambiare e renderlo dinamico per la ricerca seri
      /*  axios
        .get(
          `${this.api.basaUri}search/movie?${this.api.key_api}&query=${query}`
        )
        .then((result) => {
          this.moviesList = result.data.results;
        })
        .catch((error) => {
          console.log(error);
        }); */
      axios
        .get(
          `https://api.themoviedb.org/3/search/movie?api_key=12dd05e7d86d7822ce2c8e30b16accee&query=${query}`
        )
        .then((result) => {
          this.moviesList = result.data.results;
          console.log("array film dalla chiamata", this.moviesList.data);
        })
        .catch((error) => {
          console.log(error);
        });
    },
  },
  computed: {},
};
</script>

<style lang="scss">
@import "./components/style/main-style.scss";
</style>
