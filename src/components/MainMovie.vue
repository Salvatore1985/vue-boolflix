<template>
  <section class="mb-5 my-container">
    <div class="cover-all h-100">
      <img
        class="my-cover"
        :src="`https://image.tmdb.org/t/p/w342${movieCoverPoster}`"
        :alt="movieTitle"
      />
    </div>
    <section class="description w-100">
      <div class="">
        <img
          class="my-cover img-fluid"
          :src="`https://image.tmdb.org/t/p/w342${movieCover}`"
          :alt="movieTitle"
        />
      </div>
      <div class="overflow-auto">
        <ul>
          <li><span class="text-danger">Tittolo: </span>{{ movieTitle }}</li>
          <li>
            <span class="text-danger">Titolo Originale: </span
            >{{ movieOriginal_title }}
          </li>
          <li v-if="movieOriginal_title !== 'en'">
            <span class="text-danger">Lingua: </span>
            <img
              :src="`https://flagcdn.com/24x18/${movieOriginal_language}.png`"
              :alt="movieOriginal_title"
            />
          </li>
          <li v-else>
            <span class="text-danger">Lingua: </span>
            <span class="text-uppercase"> {{ movieOriginal_language }} </span>
          </li>
          <li>
            <span class="text-danger">Voto: </span>

            <span
              v-for="(star, index) in getVotes(movieVote_average)"
              :key="index + 'star' + 'solid'"
              ><font-awesome-icon
                icon="fa-solid fa-star"
                class="text-warning"
              />
            </span>
            <span
              v-for="(star, index) in 5 - getVotes(movieVote_average)"
              :key="index + 'star' + 'regular'"
            >
              <font-awesome-icon
                icon="fa-regular fa-star"
                class="text-warning"
              />
            </span>
          </li>
          <li>
            <span class="text-danger">Descrizione: </span>{{ movieOverview }}
          </li>
        </ul>
      </div>
    </section>
  </section>
</template> 

<script>
export default {
  name: "HomeMain",
  props: [
    "movieTitle",
    "movieOriginal_title",
    "movieOriginal_language",
    "movieVote_average",
    "movieCover",
    "movieOverview",
    "movieCoverPoster",
  ],
  data() {
    return {
      /*  flags: [], */
    };
  },
  created() {},
  methods: {
    getVotes(vote) {
      return Math.ceil(vote / 2);
    },
  },
  computed: {},
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>
@import "../components/style/main-style.scss";
section {
  background: linear-gradient(to bottom, $color_cards, $brand_secondary);
  /* background-color: $color_cards; */
  width: calc(100% / $nDivision_cards);
  height: 600px;
  border: 1px solid $brand_secondary;
}
</style>
