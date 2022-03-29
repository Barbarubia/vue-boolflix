<template>
  <header>
    <nav>
      <label for="search-title">
        <input type="text" name="search-title" id="search-title" placeholder="Digita il titolo...">
      </label>
      <button @click="ricercaTitolo">Cerca</button>
    </nav>
    <hr>
  </header>
</template>

<script>
export default {
  name: 'HeaderBoolflix',
  methods: {
    ricercaTitolo () {
      return console.log('prova bottone')
    }
  }
}
</script>

<style lang="scss" scoped>

</style>
