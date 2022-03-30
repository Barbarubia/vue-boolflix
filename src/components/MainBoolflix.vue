<template>
  <main>
    <div class="container">
      <h2 v-if="arrayMovies.length != 0">Film</h2>
      <card-movie
        v-for="movie in arrayMovies"
        :key="movie.it"
        :movie-data="movie"
      />
      <h2 v-if="arraySeries.length != 0">Serie TV</h2>
      <card-serie
        v-for="serie in arraySeries"
        :key="serie.it"
        :serie-data="serie"
      />
    </div>
  </main>
</template>

<script>
import CardMovie from './CardMovie.vue'
import CardSerie from './CardSerie.vue'

export default {
  name: 'MainBoolflix',
  components: {
    CardMovie,
    CardSerie
  },
  props: {
    arrayMovies: Array,
    arraySeries: Array
  }
}
</script>

<style lang="scss" scoped>
main {
  margin-top: 5rem;
}
</style>
