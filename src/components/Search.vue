<template>
  <div>
    <input
      type="text"
      placeholder="Inserisci qui"
      v-model.trim="inputSearch"
      @keyup.enter="emitSearch"
    />
    <button @click="emitSearch" class="bg-light" type="submit">Cerca</button>
  </div>
</template>

<script>
export default {
  name: "SearchHome",

  data() {
    return {
      inputSearch: "",
    };
  },
  created() {},
  methods: {
    emitSearch() {
      this.$emit("search", this.inputSearch);
      console.log("Input/Button Search, cliccato");
      this.inputSearch = "";
    },
  },
  computed: {},
};
</script>

<style lang="scss">
@import "../components/style/main-style.scss";
</style>
