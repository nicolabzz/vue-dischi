<template>
  <header>

    <!-- logo  -->
    <div class="logo">
      <img src="@/assets/logo-spotify.png" alt="">
    </div>

    <!-- gener selector section -->
    <label for="select-genres">
      <select
        id="select-genres"
        name="genres"
        @change="genreChange"
        v-model="genreFilter"
      >
        <option value="all">
          All genres
        </option>
        <option
          v-for="genre in genresList"
          :key="genre"
          :value="genre"
        >
        {{ genre }}
        </option>
      </select>
    </label>
  </header>
</template>

<script>
export default {
  name: 'HesderaPage',
  data() {
    return {
      genreFilter: 'all',
    };
  },
  // props: {
  //   genresList: {
  //     type: Array,
  //     required: true,
  //   },
  // },
  props: {
    genresList: Array,
  },
  methods: {
    genreChange() {
      this.$emit('changedGenre', this.genreFilter);
    },
    // authorChange() {
    //   this.$emit('changAuthor', this.authorFilter);
    // },
  },
};
</script>

<style lang="scss" scoped>
header {
  background-color: #2E3A46;
  height: 50px;
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.logo {
  // border: 2px solid green;
  height: 50px;
  width: 50px;
  object-fit: cover;
  cursor: pointer;

  img {
    width: 100%;
    padding: .3rem;
  }

}

label {
  // border: 2px solid green;
  display: flex;
  justify-content: center;
  width: 200px;
  height: 40px;
}

select {
  // border: 2px solid yellow;
  border-radius: 5px;
  width: 150px;
  cursor: pointer;
  background-color: #1E2D3B;
  color: white;
  font-family: 'Nunito Sans', sans-serif;
  font-weight: 800;
}

// option {
// }

</style>
