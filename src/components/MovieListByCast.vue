<template>
  <div>
    <h1>Filmy według obsady</h1>
    <ul v-for="item in items" :key="item">
      <h4 v-if="getMoviesByCast(item).length !== 0">{{ item }}</h4>
      <li v-for="(movie,index) in getMoviesByCast(item) " v-bind:key="index">
        {{ movie.title }}
      </li>
    </ul>
  </div>
</template>

<script>
import movies from '../assets/movies/movies.json'
import {_} from 'vue-underscore';

let moviesList = _.first(movies, 100);

export default {
  name: "MovieListByCast",
  data() {
    return {
      items: this.getCasts()
    };
  },
  methods: {
    getMoviesByCast: function (cast) {
      return _.filter(moviesList, function (movie) {
        return _.contains(movie.cast, cast)
      });
    },
    getCasts: function () {
      let casts = new Set()
      for (let movie of moviesList) {
        for(let cast of movie.cast){
          casts.add(cast)
        }
      }
      return casts
    }
  },
}
</script>

<style scoped>

</style>