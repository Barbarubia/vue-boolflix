<template>
  <main>
    <card-titolo
      v-for="titolo in arrayTitoli"
      :key="titolo.it"
      :titolo-data="titolo"
    />
  </main>
</template>

<script>
import CardTitolo from './CardTitolo.vue'

export default {
  name: 'MainBoolflix',
  components: {
    CardTitolo
  },
  props: {
    arrayTitoli: Array
  }
}
</script>

<style lang="scss" scoped>

</style>
