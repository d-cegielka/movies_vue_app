<template>
  <b-container>
    <h1>Baza filmów</h1>
    <SearchEngine/>
    <MovieTable/>
    <MovieListByGenre/>
    <MovieListByCast/>
  </b-container>
</template>

<script>
import SearchEngine from './components/SearchEngine.vue'
import MovieTable from "@/components/MovieTable";
import MovieListByGenre from "@/components/MovieListByGenre";
import MovieListByCast from "@/components/MovieListByCast";

export default {
  name: 'App',
  components: {
    MovieListByCast,
    MovieListByGenre,
    SearchEngine,
    MovieTable
  }
}
</script>

<style>

</style>
