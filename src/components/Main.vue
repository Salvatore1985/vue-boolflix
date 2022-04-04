<template>
  <main class="overflow-auto">
    <div class="container p-5">
      <div class="row">
        <!-- <div class="col-12 text-danger">{{ searchAll }}</div> -->
        <div class="col-12 text-white">
          <!--     <ul v-for="(list, index) in listFilm" :key="index">
            <li>{{ listFilm }}</li>
          </ul> -->
        </div>
      </div>
    </div>
  </main>
</template> 

<script>
/* import axios from "axios"; */
export default {
  name: "HomeMain",

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
<style scoped lang="scss">
@import "../components/style/main-style.scss";
main {
  height: calc($main_home - $header_home);
  background-color: $brand_secondary;
}
</style>
