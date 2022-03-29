<template>
  <main>
    Qui inizia il main
    <h1>{{ stringaTitoloCercato }}</h1>
  </main>
</template>

<script>
export default {
  name: 'MainBoolflix',
  props: {
    stringaTitoloCercato: String
  },
  data () {
    return {

    }
  }
}
</script>

<style lang="scss" scoped>

</style>
