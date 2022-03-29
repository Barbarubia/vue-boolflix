<template>
  <div>
    <p>Titolo: {{ titoloData.title }}</p>
    <p>Titolo Originale: {{ titoloData.original_title }}</p>
    <p>Lingua: {{ titoloData.original_language }}</p>
    <p>Voto: {{ titoloData.vote_average }}</p>
  </div>
</template>

<script>
export default {
  name: 'CardTitolo',
  props: {
    titoloData: Object
  }
}
</script>

<style lang="scss" scoped>

</style>
