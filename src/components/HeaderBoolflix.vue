<template>
  <header>
    <nav>
      <label for="search-title">
        <input type="text" name="search-title" id="search-title" v-model="titoloCercato" placeholder="Digita il titolo...">
      </label>
      <button @click="ricercaTitolo">Cerca</button>
    </nav>
    <hr>
  </header>
</template>

<script>
export default {
  name: 'HeaderBoolflix',
  data () {
    return {
      titoloCercato: ''
    }
  },
  methods: {
    ricercaTitolo () {
      this.$emit('sendTitolo', this.titoloCercato)
      // console.log(this.titoloCercato)
    }
  }
}
</script>

<style lang="scss" scoped>

</style>
