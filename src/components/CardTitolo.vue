<template>
  <ul>
    <li>
      <p>Titolo: {{ titoloData.title }}</p>
      <p>Titolo Originale: {{ titoloData.original_title }}</p>
      <p>Lingua: {{ titoloData.original_language }} <img :src="findFlag()" :alt="titoloData.original_language"></p>
      <p>Voto: {{ titoloData.vote_average }}</p>
    </li>
  </ul>
</template>

<script>
export default {
  name: 'CardTitolo',
  props: {
    titoloData: Object
  },
  methods: {
    findFlag () {
      if (this.titoloData.original_language === 'de' || this.titoloData.original_language === 'en' || this.titoloData.original_language === 'es' || this.titoloData.original_language === 'fr' || this.titoloData.original_language === 'it') {
        return require('../assets/img/flags/' + this.titoloData.original_language + '.png')
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
