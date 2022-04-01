<template>
  <header>
    <div class="container">
      <div class="row" id="row-header">
        <div class="col-12 d-flex justify-content-between align-items-center">
          <div class="text-uppercase">
            <h1>boolflix</h1>
          </div>
          <Search @search="getMovies" />
        </div>
      </div>
    </div>
  </header>
</template>

<script>
import Search from "./Search.vue";
export default {
  name: "HomeHeader",
  /*  props: ["inputSearch"], */
  components: {
    Search,
  },

  data() {
    return {
      searchAll: "",
    };
  },
  created() {},
  methods: {
    getMovies(query) {
      console.log("Input/Button Search recuperato ", query);
    },
  },
  computed: {},
};
</script>


<style scoped lang="scss">
@import "../components/style/main-style.scss";
header {
  height: $header_home;
  background-color: $color_primary;
  #row-header {
    height: $header_home;
  }
  div {
    h1 {
      color: #e50914;
    }
  }
}
</style>
