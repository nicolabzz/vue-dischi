<template>
  <div id="app">
    <HeaderPage
      :genres-list="genresList"
      @changedGenre="genreChange"
    />
    <PageMain
      :genre-filter="genreFilter"
      @genresReady="getGenresList"
    />
  </div>
</template>

<script>
import HeaderPage from './components/HeaderPage.vue';
import PageMain from './components/PageMain.vue';

export default {
  name: 'App',
  components: {
    PageMain,
    HeaderPage,
  },
  data() {
    return {
      genresList: [],
      genreFilter: 'all',
    };
  },
  methods: {
    getGenresList(genresList) {
      this.genresList = genresList;
    },
    genreChange(genreFilter) {
      console.log(genreFilter);
      this.genreFilter = genreFilter;
    },
  },
};
</script>

<style lang="scss">
@import url('https://fonts.googleapis.com/css2?family=Nunito+Sans:wght@300;800&display=swap');

* {
  padding: 0;
  margin:0;
  box-sizing: border-box;
}
</style>
