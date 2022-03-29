<template>
  <header>
    <nav>
      <label for="search-title">
        <input @keyup.enter="$emit('sendTitolo', titoloCercato)" v-model="titoloCercato" type="text" name="search-title" id="search-title" placeholder="Digita il titolo...">
      </label>
      <button @click="$emit('sendTitolo', titoloCercato)">Cerca</button>
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
  }
}
</script>

<style lang="scss" scoped>

</style>
