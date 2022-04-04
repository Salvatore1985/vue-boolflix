<template>
  <section class="mb-5 my-container">
    <div class="cover-all h-100">
      <img
        class="my-cover"
        :src="`https://image.tmdb.org/t/p/w342${tvCoverPoster}`"
        :alt="tvTitle"
      />
    </div>
    <section class="description w-100">
      <div class="h-50">
        <img
          class="my-cover"
          :src="`https://image.tmdb.org/t/p/w342${tvCover}`"
          :alt="tvTitle"
        />
      </div>
      <div class="h-50 overflow-auto">
        <ul>
          <li><span class="text-danger">Tittolo: </span>{{ tvTitle }}</li>
          <li>
            <span class="text-danger">Titolo Originale: </span>{{ tvTitle }}
          </li>
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
          <li>
            <span class="text-danger">Descrizione: </span>{{ tvOverview }}
          </li>
        </ul>
      </div>
    </section>
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
    "tvCover",
    "tvOverview",
    "tvCoverPoster",
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
  background: linear-gradient(to bottom, $color_cards, $brand_secondary);
  /*   background-color: $color_cards; */
  width: calc(100% / $nDivision_cards);
  height: 600px;
  border: 1px solid $brand_secondary;
}
</style>
