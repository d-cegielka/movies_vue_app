<template>
  <div>
    <h1>Filmy według gatunku</h1>
    <ol v-for="item in items" :key="item">
        <h4 v-if="getMoviesByGenre(item).length !== 0">{{item}}</h4>
        <li v-for="(movie,index) in getMoviesByGenre(item) " :key="index" >
          {{movie.title}}
        </li>
    </ol>
  </div>
</template>

<script>
import genres from '../assets/movies/genres.json'
import movies from '../assets/movies/movies.json'
import {_} from 'vue-underscore';

let moviesList = _.first(movies, 100);

export default {
name: "MovieListByGenre",
  data(){
    return {
    items: genres
  };
  },
 methods:{
  getMoviesByGenre: function (genre) {
    return _.filter(moviesList,function (movie) {
     return _.contains(movie.genres,genre)
    });
  }
 }
}
</script>

<style scoped>

</style>
