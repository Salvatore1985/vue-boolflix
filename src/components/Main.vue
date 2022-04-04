<template>
  <section class="p-5">
    <!-- <div class="col-12 text-white"> -->
    <ul>
      <li><span class="text-danger">Tittolo: </span> {{ movieTitle }}</li>
      <li>
        <span class="text-danger">Titolo Originale: </span
        >{{ movieOriginal_title }}
      </li>
      <li>
        <span class="text-danger">Lingua: </span>{{ movieOriginal_languagee }}
      </li>
      <li><span class="text-danger">Voto: </span>{{ movieVote_average }}</li>
    </ul>
    <!--   </div> -->
  </section>
</template> 

<script>
/* import axios from "axios"; */
export default {
  name: "HomeMain",
  props: [
    "movieTitle",
    "movieOriginal_title",
    "movieOriginal_languagee",
    "movieVote_average",
  ],
  data() {
    return {
      listFilm: [],
      apiList:
        "https://api.themoviedb.org/3/search/movie?api_key=12dd05e7d86d7822ce2c8e30b16accee&query",
      searchFilm: "ritorno",
    };
  },
  created() {
    /*  axios
      .get(`${this.apiList}=${this.searchFilm}`)
      .then((result) => {
        this.listFilm = result.data;
        console.log("questa e la lista dei film ", this.listFilm);
        //const resultFilm = result.data;
        //.log(resultFilm);
      })
      .catch((error) => {
        console.log(error);
      }); */
  },
  methods: {},
  computed: {},
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>
@import "../components/style/main-style.scss";
</style>
