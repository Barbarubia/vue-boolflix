<template>
  <ul>
    <li class="card-titolo">
      <div class="poster">
        <img :src="findPoster()" :alt="movieData.title">
        <h4 class="no-poster">{{ movieData.title }}</h4>

      </div>
      <div class="info-titolo">
        <h4>{{ movieData.title }}</h4>
        <h5>(Original: {{ movieData.original_title }})</h5>
        <img class="img-flag" :src="findFlag()" :alt="movieData.original_language">
        <div class="stars">
          <span v-if="ratingFive(movieData.vote_average) > 0"><font-awesome-icon v-for="counter in ratingFive(movieData.vote_average)" :key="counter" icon="fa-solid fa-star" /></span>
          <span v-if="ratingFive(movieData.vote_average) < 5"><font-awesome-icon v-for="counter in (5 - ratingFive(movieData.vote_average))" :key="counter" icon="fa-regular fa-star" /></span>
        </div>
      </div>
    </li>
  </ul>
</template>

<script>
export default {
  name: 'CardMovie',
  props: {
    movieData: Object
  },
  methods: {
    findFlag () {
      if (this.movieData.original_language === 'de' || this.movieData.original_language === 'en' || this.movieData.original_language === 'es' || this.movieData.original_language === 'fr' || this.movieData.original_language === 'it') {
        return require('../assets/img/flags/' + this.movieData.original_language + '.png')
      } else {
        return require('../assets/img/flags/unknown.png')
      }
    },
    findPoster () {
      if (this.movieData.poster_path) {
        return 'https://image.tmdb.org/t/p/w342' + this.movieData.poster_path
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
ul {
  list-style: none;
  display: inline-block;
  // margin: 0 .5rem;
  width: calc(100% / 5 - 1rem);
}

.card-titolo {
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
