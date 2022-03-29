<template>
  <main>
    <h1 v-if="arrayMovies.length != 0">Film</h1>
    <card-movie
      v-for="movie in arrayMovies"
      :key="movie.it"
      :movie-data="movie"
    />
    <h1 v-if="arraySeries.length != 0">Serie TV</h1>
    <card-serie
      v-for="serie in arraySeries"
      :key="serie.it"
      :serie-data="serie"
    />
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

</style>
