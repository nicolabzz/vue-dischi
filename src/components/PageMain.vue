<template>
  <div class="container-main">
    <div class="container-cener">
      <CardMovie
      v-for="objMovie in arrDiscsFiltered"
      :key="objMovie.title"
      :movie-info="objMovie"
    />
  </div>
    </div>
    <!-- <ul>
      <li
      v-for="genre in arrGenres"
      :key="genre"
      >
      {{genre}}
    </li>
    </ul> -->
</template>

<script>
import axios from 'axios';
import CardMovie from './CardMovie.vue';

export default {
  name: 'PageMain',
  components: {
    CardMovie,
  },
  props: {
    genreFilter: String,
  },
  data() {
    return {
      urlApi: 'https://flynn.boolean.careers/exercises/api/array/music',
      arrDiscs: null,
    };
  },
  computed: {

    arrGenres() {
      const arrGenres = [];
      if (this.arrDiscs) {
        this.arrDiscs.forEach((objDisc) => {
          if (!arrGenres.includes(objDisc.genre)) {
            arrGenres.push(objDisc.genre);
          }
        });
      }
      return arrGenres;
    },

    arrDiscsFiltered() {
      if (this.genreFilter === 'all') {
        return this.arrDiscs;
      }
      return this.arrDiscs.filter((objDisc) => objDisc.genre === this.genreFilter);
    },
  },

  watch: {
    arrGenres(newValue) {
      this.$emit('genresReady', newValue);
    },
  },
  created() {
    axios.get(this.urlApi)
      .then((axiosResponse) => {
        this.arrDiscs = axiosResponse.data.response;
      });
  },
};
</script>

<style lang="scss" scoped>
.container-main {
  // border: 2px solid brown;
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: #1E2D3B;
  height: 879px;
  width: 100%;
}

.container-cener {
  // border: 2px solid yellow;
  display: flex;
  flex-wrap: wrap;
  width: 1100px;
  max-height: 879px;

}
</style>
