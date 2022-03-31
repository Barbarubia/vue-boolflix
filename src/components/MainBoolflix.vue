<template>
  <main>
    <div class="container">
      <div class="container-movies">
        <h2 v-if="arrayMovies.length != 0">Film trovati per la ricerca "{{ stringaRicerca }}"</h2>
        <card-boolflix
          v-for="movie in arrayMovies"
          :key="movie.it"
          :ricerca-data="movie"
          :array-genres-movies="arrayGenresMovies"
        />
      </div>
      <div class="container-series">
        <h2 v-if="arraySeries.length != 0">Serie TV trovate per la ricerca "{{ stringaRicerca }}"</h2>
        <card-boolflix
          v-for="serie in arraySeries"
          :key="serie.it"
          :ricerca-data="serie"
          :array-genres-series="arrayGenresSeries"
        />
      </div>
    </div>
  </main>
</template>

<script>
import CardBoolflix from './CardBoolflix.vue'

export default {
  name: 'MainBoolflix',
  components: {
    CardBoolflix
  },
  props: {
    arrayMovies: Array,
    arraySeries: Array,
    arrayGenresMovies: Array,
    arrayGenresSeries: Array,
    stringaRicerca: String
  }
}
</script>

<style lang="scss" scoped>
main {
  margin-top: 5rem;
}

.container-series {
  margin-top: 5rem;
}
</style>
