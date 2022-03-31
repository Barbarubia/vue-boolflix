<template>
  <div id="app">
    <header-boolflix @sendTitolo="readTitoloCercato"/>
    <main-boolflix :array-movies="arrMovies" :array-series="arrSeries" :array-genres-movies="arrGenresMovies" :array-genres-series="arrGenresSeries" :stringa-ricerca="titoloCercato"/>
  </div>
</template>

<script>
import HeaderBoolflix from './components/HeaderBoolflix.vue'
import MainBoolflix from './components/MainBoolflix.vue'
import axios from 'axios'

export default {
  name: 'App',
  components: {
    HeaderBoolflix,
    MainBoolflix
  },
  data () {
    return {
      titoloCercato: '',
      apiBaseUrl: 'https://api.themoviedb.org/3/',
      apiKey: 'bc3f3089deff2ed15d9a285827988a57',
      arrMovies: [],
      arrSeries: [],
      arrGenresMovies: [],
      arrGenresSeries: []
    }
  },
  methods: {
    readTitoloCercato (titoloDigitato) {
      this.titoloCercato = titoloDigitato
      // console.log(this.titoloCercato)
      if (this.titoloCercato.trim() !== '') {
        axios.get(this.apiBaseUrl + 'search/movie/?api_key=' + this.apiKey + '&query=' + this.titoloCercato)
          .then(risposta => {
            this.arrMovies = risposta.data.results
            // console.log(this.arrMovies)
            if (this.arrMovies.length !== 0) {
              axios.get(this.apiBaseUrl + 'genre/movie/list?api_key=' + this.apiKey)
                .then(risposta => {
                  this.arrGenresMovies = risposta.data.genres
                  // console.log(this.arrGenresMovies)
                })
            }
          })
        axios.get(this.apiBaseUrl + 'search/tv/?api_key=' + this.apiKey + '&query=' + this.titoloCercato)
          .then(risposta => {
            this.arrSeries = risposta.data.results
            // console.log(this.arrSeries)
            if (this.arrSeries.length !== 0) {
              axios.get(this.apiBaseUrl + 'genre/tv/list?api_key=' + this.apiKey)
                .then(risposta => {
                  this.arrGenresSeries = risposta.data.genres
                  // console.log(this.arrGenresSeries)
                })
            }
          })
      } else {
        this.arrMovies = []
        this.arrSeries = []
      }
    }
  }
}
</script>

<style lang="scss">
@import "./assets/scss/style.scss";

body {
  background-color: $main-bg;
  color: white;
}
</style>
