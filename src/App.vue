<template>
  <div id="app">
    <header-boolflix @sendTitolo="readTitoloCercato"/>
    <main-boolflix :array-movies="arrMovies" :array-series="arrSeries"/>
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
      arrSeries: []
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
          })
        axios.get(this.apiBaseUrl + 'search/tv/?api_key=' + this.apiKey + '&query=' + this.titoloCercato)
          .then(risposta => {
            this.arrSeries = risposta.data.results
            // console.log(this.arrSeries)
          })
      }
    }
  }
}
</script>

<style lang="scss">

</style>
