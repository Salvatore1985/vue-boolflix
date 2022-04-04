<template>
  <header>
    <div class="container">
      <div class="row" id="row-header">
        <div class="col-12 d-flex justify-content-between align-items-center">
          <div class="text-uppercase">
            <h1>boolflix</h1>
          </div>
          <Search @search="getSearch" />
        </div>
      </div>
    </div>
  </header>
</template>

<script>
import Search from "./Search.vue";
export default {
  name: "HomeHeader",

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
    getSearch(search) {
      console.log("Input/Button Search recuperato ", search, " nell'Header");
      this.$emit("search", search);
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
