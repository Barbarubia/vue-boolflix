<template>
  <header>
    <nav>
      <label for="search-title">
        <input @keyup.enter="searchTitolo" v-model="titoloCercato" type="text" name="search-title" id="search-title" placeholder="Digita il titolo...">
      </label>
      <button @click="searchTitolo">Cerca</button>
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
    searchTitolo () {
      this.$emit('sendTitolo', this.titoloCercato)
      this.titoloCercato = ''
    }
  }
}
</script>

<style lang="scss" scoped>

</style>
