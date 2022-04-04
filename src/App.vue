<template>
  <div id="app">
    <Header @search="getMovies" />
    <main class="overflow-auto">
      <section>
        <div class="container p-5">
          <div class="row">
            <div class="col-12 text-white d-flex flex-wrap">
              <Main
                v-for="movie in moviesList"
                :key="movie.id"
                :movieTitle="movie.title"
                :movieOriginal_title="movie.original_title"
                :movieOriginal_languagee="movie.original_language"
                :movieVote_average="movie.vote_average"
              />
            </div>
          </div>
        </div>
      </section>
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
      axios
        .get(
          `${this.api.basaUri}search/movie?api_key=${this.api.key_api}&query=${query}`
        )
        .then((result) => {
          this.moviesList = result.data.results;
          console.log("array film dalla chiamata", result.data.results);
        })
        .catch((error) => {
          console.log(error);
          console.log(this.api.basaUri);
          console.log(this.api.key_api);
          console.log(query);
          console.log(
            `${this.api.basaUri}search/movie?${this.api.key_api}&query=${query}`
          );
        });
    },
  },
  computed: {},
};
</script>

<style lang="scss">
@import "./components/style/main-style.scss";
main {
  height: calc($main_home - $header_home);
  background-color: $brand_secondary;
}
</style>
