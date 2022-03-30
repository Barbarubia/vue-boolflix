<template>
  <ul>
    <li>
      <img v-if="movieData.poster_path" :src="'https://image.tmdb.org/t/p/w342' + movieData.poster_path" :alt="movieData.title">
      <p>Titolo: {{ movieData.title }}</p>
      <p>Titolo Originale: {{ movieData.original_title }}</p>
      <p>Lingua: {{ movieData.original_language }} <img class="img-flag" :src="findFlag()" :alt="movieData.original_language"></p>
      <p>Voto: {{ ratingFive(movieData.vote_average) }}</p>
      <span v-if="ratingFive(movieData.vote_average) > 0"><font-awesome-icon v-for="counter in ratingFive(movieData.vote_average)" :key="counter" icon="fa-solid fa-star" /></span>
      <span v-if="ratingFive(movieData.vote_average) < 5"><font-awesome-icon v-for="counter in (5 - ratingFive(movieData.vote_average))" :key="counter" icon="fa-regular fa-star" /></span>
    </li>
  </ul>
</template>

<script>
export default {
  name: 'CardMovie',
  props: {
    movieData: Object
  },
  methods: {
    findFlag () {
      if (this.movieData.original_language === 'de' || this.movieData.original_language === 'en' || this.movieData.original_language === 'es' || this.movieData.original_language === 'fr' || this.movieData.original_language === 'it') {
        return require('../assets/img/flags/' + this.movieData.original_language + '.png')
      } else {
        return require('../assets/img/flags/unknown.png')
      }
    },
    ratingFive (vote) {
      return Math.round(vote / 2)
    }
  }
}
</script>

<style lang="scss" scoped>
.img-flag {
  height: 1rem;
}
</style>
