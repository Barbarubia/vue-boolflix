<template>
  <div id="app">
    <header-boolflix @sendTitolo="setTitoloCercato"/>
    <main-boolflix :stringa-titolo-cercato="titoloCercato"/>
  </div>
</template>

<script>
import HeaderBoolflix from './components/HeaderBoolflix.vue'
import MainBoolflix from './components/MainBoolflix.vue'

export default {
  name: 'App',
  components: {
    HeaderBoolflix,
    MainBoolflix
  },
  data () {
    return {
      titoloCercato: ''
    }
  },
  methods: {
    setTitoloCercato (titoloDigitato) {
      this.titoloCercato = titoloDigitato
      console.log(this.titoloCercato)
    }
  }
}
</script>

<style lang="scss">

</style>
