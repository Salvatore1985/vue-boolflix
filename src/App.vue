<template>
  <div id="app">
    <Header @search="search" />
    <main class="overflow-auto">
      <!--  <div @click="getFlags" class="text-center text-danger text-uppercase">
        prova
      </div> -->
      <section>
        <div class="container-fluid p-5">
          <div class="row">
            <div class="col-12 shadow" id="film">
              <h2 class="text-danger text-uppercase p-4">
                Film
                <span v-if="moviesList.length > 0"
                  >Trovati {{ moviesList.length }}
                </span>
              </h2>
            </div>
            <div class="col-12 text-white d-flex flex-wrap">
              <MainMovie
                v-for="movie in moviesList"
                :key="movie.id"
                :movieTitle="movie.title"
                :movieOriginal_title="movie.original_title"
                :movieOriginal_language="movie.original_language"
                :movieVote_average="movie.vote_average"
                :movieCover="movie.backdrop_path"
                :movieOverview="movie.overview"
                :movieCoverPoster="movie.poster_path"
              />
            </div>
            <div class="col-12 shadow" id="serie">
              <h2 class="text-danger text-uppercase p-4">
                Serie Tv
                <span v-if="tvList.length > 0"
                  >Trovati {{ tvList.length }}
                </span>
              </h2>
            </div>
            <div
              class="col-12 text-white d-flex flex-wrap justify-content-center"
            >
              <MainTv
                v-for="tv in tvList"
                :key="tv.id"
                :tvTitle="tv.name"
                :tvOriginal_title="tv.original_name"
                :tvOriginal_language="tv.original_language"
                :tvVote_average="tv.vote_average"
                :tvCover="tv.backdrop_path"
                :tvCoverPoster="tv.poster_path"
                :tvOverview="tv.overview"
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
import MainMovie from "./components/MainMovie.vue";
import MainTv from "./components/MainTv.vue";

import { library } from "@fortawesome/fontawesome-svg-core";
import { faUserSecret } from "@fortawesome/free-solid-svg-icons";

library.add(faUserSecret);

export default {
  name: "App",
  components: {
    Header,
    MainMovie,
    MainTv,
  },
  data() {
    return {
      flags: [],
      moviesList: [],
      tvList: [],
      api: {
        basaUri: "https://api.themoviedb.org/3/",
        key_api: "12dd05e7d86d7822ce2c8e30b16accee",
        imgHttps: "https://image.tmdb.org/t/p",
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
          console.log("array completo ", this.moviesList);
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
    getTv(query) {
      console.log("Search recuperato serie tv ", query, " nell'App");
      if (!query) this.tvList = [];

      axios
        .get(
          `${this.api.basaUri}search/tv?api_key=${this.api.key_api}&query=${query}`
        )
        .then((result) => {
          this.tvList = result.data.results;
          console.log("array serie tv dalla chiamata", result.data.results);
          console.log("array completo tv ", this.tvList);
        })
        .catch((error) => {
          console.log(error);
          console.log(this.api.basaUri);
          console.log(this.api.key_api);
          console.log(query);
          console.log(
            `${this.api.basaUri}search/tv?${this.api.key_api}&query=${query}`
          );
        });
    },
    search(query) {
      this.getMovies(query);
      this.getTv(query);
    },

    getFlags() {
      this.moviesList.forEach((element) => {
        const flag = element.original_language;
        if (!this.flags.includes(flag)) {
          this.flags.push(element.original_language);
        } else {
          console.log("E gia incluso nell' array");
        }
      });
      console.log("array", this.flags);
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
