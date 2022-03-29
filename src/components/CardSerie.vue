<template>
  <ul>
    <li>
      <p>Titolo: {{ serieData.name}}</p>
      <p>Titolo Originale: {{ serieData.original_name}}</p>
      <p>Lingua: {{ serieData.original_language }} <img :src="findFlag()" :alt="serieData.original_language"></p>
      <p>Voto: {{ serieData.vote_average }}</p>
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
    }
  }
}
</script>

<style lang="scss" scoped>
img {
  height: 1rem;
}
</style>
