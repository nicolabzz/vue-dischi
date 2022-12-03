<template>
  <div class="container-card">
    <div class="cards">
      <div class="img-container">
        <img :src="movieInfo.poster" alt="">
      </div>
      <h4>{{ movieInfo.title }}</h4>
      <p>{{ movieInfo.author }}</p>
      <p>{{ movieInfo.year }}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: 'CardMovie',
  props: {
    // movieInfo: {
    //   type: Object,
    //   required: true,
    // },
    movieInfo: Object,
  },
};
</script>

<style lang="scss" scoped>
.container-card {
  // border: 5px solid green;
  display: flex;
  flex: 0 0 20%;
  justify-content: center;
  // padding: 1rem;
  // align-items: center;
}
.cards {
  // border: 2px solid blue;
  display: flex;
  align-items: center;
  justify-content: space-evenly;
  flex-direction: column;
  background-color: #2E3A46;
  gap: .5rem;
  height: 330px;
  width: 186px;
  margin: 0 0 10px 0;
  border-radius: 3px;
  text-align: center;
  cursor: pointer;
  transition-duration: .25s;
  transition-timing-function: ease-in-out;

  &:hover {
    transform: scale(1.03);
  }

  .img-container {
    // border: 2px solid yellow;
    height: 150px;
    width: 150px;

    img {
      width: 100%;
    }

  }

  h4 {
    font-family: 'Nunito Sans', sans-serif;
    color: white;
    font-weight: 800;
    padding: 0 5px;
  }

  p {
    font-family: 'Nunito Sans', sans-serif;
    color: grey;
    font-weight: 300;

  }

}

</style>
