<template>
  <ul>
    <li>
      <img v-if="serieData.poster_path" :src="'https://image.tmdb.org/t/p/w342' + serieData.poster_path" :alt="serieData.name">
      <p>Titolo: {{ serieData.name}}</p>
      <p>Titolo Originale: {{ serieData.original_name}}</p>
      <p>Lingua: {{ serieData.original_language }} <img class="img-flag" :src="findFlag()" :alt="serieData.original_language"></p>
      <p>Voto: {{ ratingFive(serieData.vote_average) }}</p>
      <span v-if="ratingFive(serieData.vote_average) > 0"><font-awesome-icon v-for="counter in ratingFive(serieData.vote_average)" :key="counter" icon="fa-solid fa-star" /></span>
      <span v-if="ratingFive(serieData.vote_average) < 5"><font-awesome-icon v-for="counter in (5 - ratingFive(serieData.vote_average))" :key="counter" icon="fa-regular fa-star" /></span>
    </li>
  </ul>
</template>

<script>
export default {
  name: 'CardSerie',
  props: {
    serieData: Object
  },
  methods: {
    findFlag () {
      if (this.serieData.original_language === 'de' || this.serieData.original_language === 'en' || this.serieData.original_language === 'es' || this.serieData.original_language === 'fr' || this.serieData.original_language === 'it') {
        return require('../assets/img/flags/' + this.serieData.original_language + '.png')
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
