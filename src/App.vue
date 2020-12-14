<template>
  <b-container>
    <h1>Baza filmów</h1>
    <SearchEngine/>
    <MovieTable/>
  </b-container>
</template>

<script>
import SearchEngine from './components/SearchEngine.vue'
import MovieTable from "@/components/MovieTable";

export default {
  name: 'App',
  components: {
    SearchEngine,
    MovieTable
  }
}
</script>

<style>

</style>
