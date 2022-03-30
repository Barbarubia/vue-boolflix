<template>
  <header>
    <a class="site-title" href="#"><h1>BoolFlix</h1></a>
    <nav>
      <input @keyup.enter="searchTitolo" v-model="titoloCercato" type="text" name="search-title" id="search-title" placeholder="Digita il titolo...">
      <button @click="searchTitolo">Cerca</button>
    </nav>
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
@import "../assets/scss/partials/variables";

header {
  background-color: $header-bg;
  padding: 1rem 3rem;
  display: flex;
  justify-content: space-between;
  align-items: center;
  .site-title {
    color: $red;
    text-transform: uppercase;
    text-decoration: none;
  }
  nav {
    display: flex;
    input, button {
      height: 2rem;
      border: none;
      padding: 0 .5rem;
    }
    input {
      border-top-left-radius: .5rem;
      border-bottom-left-radius: .5rem;
    }
    button {
      background-color: $red;
      border-top-right-radius: .5rem;
      border-bottom-right-radius: .5rem;
      color: white;
      font-weight: 700;
      cursor: pointer;
    }
  }
}

</style>
