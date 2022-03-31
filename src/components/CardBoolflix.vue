<template>
  <div class="card">
    <div class="poster">
      <img :src="findPoster()" :alt="ricercaData.title ? ricercaData.title : ricercaData.name">
      <font-awesome-icon v-if="findPoster() === require('../assets/img/blank_poster.jpg')" class="no-poster icon-image" icon="fa-regular fa-image" />
      <font-awesome-icon v-if="findPoster() === require('../assets/img/blank_poster.jpg')" class="no-poster icon-ban" icon="fa-solid fa-ban" />
      <h4 class="card-titolo">{{ ricercaData.title ? ricercaData.title : ricercaData.name }}</h4>
    </div>
    <div class="info">
      <h4>{{ ricercaData.title ? ricercaData.title : ricercaData.name }}</h4>
      <h5>(Original: {{ ricercaData.original_title ? ricercaData.original_title : ricercaData.original_name }})</h5>
      <p v-if="ricercaData.genre_ids.length > 0" class="card-genres">(<span class="card-genres-list" v-for="element in getGenres()" :key="element">{{ element }}</span>)</p>
      <div class="flag-language">
        <img class="img-flag" :src="findFlag()" :alt="ricercaData.original_language">
        <p v-if="findFlag() === require('../assets/img/flags/unknown.png')">{{ ricercaData.original_language }}</p>
      </div>
      <div class="stars">
        <span v-if="ratingFive(ricercaData.vote_average) > 0"><font-awesome-icon v-for="counter in ratingFive(ricercaData.vote_average)" :key="counter" icon="fa-solid fa-star" /></span>
        <span v-if="ratingFive(ricercaData.vote_average) < 5"><font-awesome-icon v-for="counter in (5 - ratingFive(ricercaData.vote_average))" :key="counter" icon="fa-regular fa-star" /></span>
      </div>
      <!-- <p v-if="ricercaData.cast.length > 0">{{ ricercaData.cast[0].name }}</p> -->
      <p>{{ ricercaData.overview }}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: 'CardBoolflix',
  props: {
    ricercaData: Object,
    arrayGenresMovies: Array,
    arrayGenresSeries: Array
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
      return Math.ceil(vote / 2)
    },
    getGenres () {
      const genresCard = []
      if (this.ricercaData.genre_ids.length > 0) {
        this.ricercaData.genre_ids.forEach(elemento => {
          if (this.ricercaData.title) {
            this.arrayGenresMovies.forEach(genre => {
              if (genre.id === elemento) {
                genresCard.push(genre.name)
              }
            })
          } else {
            this.arrayGenresSeries.forEach(genre => {
              if (genre.id === elemento) {
                genresCard.push(genre.name)
              }
            })
          }
        })
      }
      return genresCard
    }
  }
}
</script>

<style lang="scss" scoped>
.card {
  width: calc(100% / 5 - 2rem);
  display: inline-block;
  margin: 1rem;
  position: relative;
  //stile per poster visualizzato
  .poster {
    position: relative;
    display: flex;
    img {
      width: 100%;
    }
    .no-poster {
      position: absolute;
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%);
      color: #adadad;
      &.icon-image {
        font-size: 3rem;
      }
      &.icon-ban {
        font-size: 6rem;
        opacity: .7;
      }
    }
    .card-titolo {
      position: absolute;
      bottom: 0;
      right: 0;
      background-color: rgba(0, 0, 0, 0.8);
      border-top-left-radius: 1rem;
      padding: .5rem 1rem;
      text-align: right;
      color: white;
    }
  }
  .info {
    display: none;
  }
  //stile per info aggiuntive visualizzate all'hover sul poster
  &:hover {
    .card-titolo {
      display: none;
    }
    .info {
      position: absolute;
      top: 0;
      display: flex;
      flex-direction: column;
      align-items: center;
      gap: .3rem;
      width: 100%;
      height: 100%;
      padding: 1rem;
      background-color: rgba(0, 0, 0, 0.7);
      text-align: center;
      color: white;
      overflow-y: auto;
      .card-genres {
        text-align: center;
        .card-genres-list:not(:last-of-type)::after {
          content: ', \00a0';
        }
      }
      .flag-language {
        position: relative;
        height: 1.4rem;
        .img-flag {
          height: 100%;
        }
        p {
          position: absolute;
          top: 50%;
          left: 50%;
          transform: translate(-50%, -50%);
          color: black;
          text-transform: uppercase;
        }
      }
      .stars {
        color: yellow;
      }
      p {
        text-align: left;
        font-size: .8rem;
      }
    }
  }
}

@media screen and (max-width: 750px) {
  .card {
    width: calc(100% / 3 - 2rem);
  }
}

@media screen and (max-width: 450px) {
  .card {
    width: calc(100% - 2rem);
  }
}
</style>
