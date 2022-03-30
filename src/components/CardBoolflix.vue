<template>
  <div class="card-titolo">
    <div class="poster">
      <img :src="findPoster()" :alt="ricercaData.title ? ricercaData.title : ricercaData.name">
      <h4 class="no-poster">{{ ricercaData.title ? ricercaData.title : ricercaData.name }}</h4>

    </div>
    <div class="info-titolo">
      <h4>{{ ricercaData.title ? ricercaData.title : ricercaData.name }}</h4>
      <h5>(Original: {{ ricercaData.original_title ? ricercaData.original_title : ricercaData.original_name }})</h5>
      <img class="img-flag" :src="findFlag()" :alt="ricercaData.original_language">
      <div class="stars">
        <span v-if="ratingFive(ricercaData.vote_average) > 0"><font-awesome-icon v-for="counter in ratingFive(ricercaData.vote_average)" :key="counter" icon="fa-solid fa-star" /></span>
        <span v-if="ratingFive(ricercaData.vote_average) < 5"><font-awesome-icon v-for="counter in (5 - ratingFive(ricercaData.vote_average))" :key="counter" icon="fa-regular fa-star" /></span>
      </div>
      <p>{{ ricercaData.overview }}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: 'CardBoolflix',
  props: {
    ricercaData: Object
  },
  methods: {
    findFlag () {
      if (this.ricercaData.original_language === 'de' || this.ricercaData.original_language === 'en' || this.ricercaData.original_language === 'es' || this.ricercaData.original_language === 'fr' || this.ricercaData.original_language === 'it') {
        return require('../assets/img/flags/' + this.ricercaData.original_language + '.png')
      } else {
        return require('../assets/img/flags/unknown.png')
      }
    },
    findPoster () {
      if (this.ricercaData.poster_path) {
        return 'https://image.tmdb.org/t/p/w342' + this.ricercaData.poster_path
      } else {
        return require('../assets/img/blank_poster.jpg')
      }
    },
    ratingFive (vote) {
      return Math.round(vote / 2)
    }
  }
}
</script>

<style lang="scss" scoped>
.card-titolo {
  width: calc(100% / 5 - 2rem);
  display: inline-block;
  margin: 1rem;
  position: relative;
  text-align: center;
  .info-titolo {
    opacity: 0;
    background-color: rgba(0, 0, 0, 0.6);
    width: 100%;
    height: 100%;
    position: absolute;
    top: 0;
    left: 50%;
    transform: translateX(-50%);
    display: flex;
    flex-direction: column;
    color: white;
    overflow-y: auto;
  }
  &:hover {
    .info-titolo {
      opacity: 1;
    }
  }
}

.poster img{
  width: 100%;
}

.no-poster {
  position: absolute;
  bottom: 0;
  right: 0;
  background-color: rgba(0, 0, 0, 0.8);
  padding: .5rem 2rem;
  color: white;
}

.img-flag {
  height: 2rem;
}

.stars {
  color: yellow;
}
</style>
