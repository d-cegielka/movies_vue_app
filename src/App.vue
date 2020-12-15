<template>
  <b-container>
    <h1>Baza filmów</h1>
    <SearchEngine/>
    <MovieTable/>
    <MovieListByGenre/>
  </b-container>
</template>

<script>
import SearchEngine from './components/SearchEngine.vue'
import MovieTable from "@/components/MovieTable";
import MovieListByGenre from "@/components/MovieListByGenre";

export default {
  name: 'App',
  components: {
    MovieListByGenre,
    SearchEngine,
    MovieTable
  }
}
</script>

<style>

</style>
