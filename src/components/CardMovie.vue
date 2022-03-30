<template>
  <ul>
    <li>
      <img v-if="movieData.poster_path" :src="'https://image.tmdb.org/t/p/w342' + movieData.poster_path" :alt="movieData.title">
      <p>Titolo: {{ movieData.title }}</p>
      <p>Titolo Originale: {{ movieData.original_title }}</p>
      <p>Lingua: {{ movieData.original_language }} <img class="img-flag" :src="findFlag()" :alt="movieData.original_language"></p>
      <p>Voto: {{ movieData.vote_average }}</p>
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
    }
  }
}
</script>

<style lang="scss" scoped>
.img-flag {
  height: 1rem;
}
</style>
