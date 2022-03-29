<template>
  <main>
    Qui inizia il main
    <h1>{{ stringaTitoloCercato }}</h1>
  </main>
</template>

<script>
import axios from 'axios'

export default {
  name: 'MainBoolflix',
  props: {
    stringaTitoloCercato: String
  }
}
</script>

<style lang="scss" scoped>

</style>
