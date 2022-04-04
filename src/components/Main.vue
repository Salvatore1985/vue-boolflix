<template>
  <section class="p-3">
    <!-- <div class="col-12 text-white"> -->
    <ul>
      <li><span class="text-danger">Tittolo: </span></li>
      <li>
        <span class="text-danger">Titolo Originale: </span
        >{{ movieOriginal_title }}
      </li>
      <li v-if="movieOriginal_language !== 'en'">
        <span class="text-danger">Lingua: </span>
        <img
          :src="`https://flagcdn.com/24x18/${movieOriginal_language}.png`"
          :alt="movieOriginal_title"
        />
      </li>
      <li v-else>
        <span class="text-danger">Lingua: </span>
        <span> {{ movieOriginal_language }} </span>
      </li>
      <li><span class="text-danger">Voto: </span>{{ movieVote_average }}</li>
    </ul>
    <!--   </div> -->
  </section>
</template> 

<script>
/* import axios from "axios"; */
/* https://flagcdn.com
/en
/codes.json */
export default {
  name: "HomeMain",
  props: [
    "movieTitle",
    "movieOriginal_title",
    "movieOriginal_language",
    "movieVote_average",
  ],
  data() {
    return {
      /*  flags: [], */
    };
  },
  created() {},
  methods: {
    /*   getFlags() {
      this.flags.push(this.movieOriginal_languagee);
      console.log("array bandiere", this.flags);
      return this.flags;
    }, */
  },
  computed: {},
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>
@import "../components/style/main-style.scss";
section {
  background-color: $color_cards;
  width: calc(100% / 6);
  height: 500px;
  border: 1px solid $brand_secondary;
}
</style>
