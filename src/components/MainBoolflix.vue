<template>
  <main>
    <div class="container">
      <h2 v-if="arrayMovies.length != 0">Film</h2>
      <card-boolflix
        v-for="movie in arrayMovies"
        :key="movie.it"
        :ricerca-data="movie"
      />
      <h2 v-if="arraySeries.length != 0">Serie TV</h2>
      <card-boolflix
        v-for="serie in arraySeries"
        :key="serie.it"
        :ricerca-data="serie"
      />
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
    arraySeries: Array
  }
}
</script>

<style lang="scss" scoped>
main {
  margin-top: 5rem;
}
</style>
