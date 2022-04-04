<template>
  <section class="p-3">
    <ul>
      <li><span class="text-danger">Tittolo: </span>{{ tvTitle }}</li>
      <li><span class="text-danger">Titolo Originale: </span>{{ tvTitle }}</li>
      <li v-if="tvOriginal_language !== 'en'">
        <span class="text-danger">Lingua: </span>
        <img
          :src="`https://flagcdn.com/24x18/${tvOriginal_language}.png`"
          :alt="tvOriginal_title"
        />
      </li>
      <li v-else>
        <span class="text-danger">Lingua: </span>
        <span class="text-uppercase"> {{ tvOriginal_language }} </span>
      </li>
      <li><span class="text-danger">Voto: </span>{{ tvVote_average }}</li>
    </ul>
  </section>
</template> 

<script>
export default {
  name: "HomeMainTv",
  props: [
    "tvTitle",
    "tvOriginal_title",
    "tvOriginal_language",
    "tvVote_average",
  ],
  data() {
    return {};
  },
  created() {},
  methods: {},
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
