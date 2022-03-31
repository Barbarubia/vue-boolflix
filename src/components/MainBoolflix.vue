<template>
  <main>
    <div class="container">
      <div class="container-movies">
        <div class="header-ricerca" v-if="arrayMovies.length != 0">
          <h2>Film trovati per la ricerca "{{ stringaRicerca }}"</h2>
          <select name="filter-genre-movie" id="filter-genre-movie">
            <option value="" selected>Select a genre</option>
            <option v-for="genre in arrayGenresMovies" :key="genre.id" value="genre.name">{{ genre.name }}</option>
          </select>
        </div>
        <card-boolflix
          v-for="movie in arrayMovies"
          :key="movie.it"
          :ricerca-data="movie"
          :array-genres-movies="arrayGenresMovies"
        />
      </div>
      <div class="container-series">
        <div class="header-ricerca" v-if="arraySeries.length != 0">
          <h2>Serie TV trovate per la ricerca "{{ stringaRicerca }}"</h2>
          <select name="filter-genre-serie" id="filter-genre-serie">
            <option value="" selected>Select a genre</option>
            <option v-for="genre in arrayGenresSeries" :key="genre.id" value="genre.name">{{ genre.name }}</option>
          </select>
        </div>
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

.header-ricerca {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;
  align-items: center;
  select {
    height: 2rem;
    min-width: 250px;
    border-radius: .5rem;
  }
}

.container-series {
  margin-top: 5rem;
}
</style>
