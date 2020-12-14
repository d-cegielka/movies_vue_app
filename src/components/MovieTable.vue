<template>
  <div>
    <b-table condensed hover :items="items" :fields="fields">
      <template #cell(title)="data">
        {{data.item.title}}
      </template>
      <template #cell(year)="data">
        {{data.item.year}}
      </template>
      <template #cell(cast)="data">
        <span v-for="item in data.item.cast" v-bind:key="item">
          {{item + ","}}
        </span>
      </template>
      <template #cell(genres)="data">
        <span v-for="genre in data.item.genres" v-bind:key="genre">
          {{genre + ","}}
        </span>
      </template>
    </b-table>
  </div>
</template>

<script>
import movies from "../assets/movies/movies.json"
export default {
name: "MovieTable",
  data(){
    let moviesList = movies
    return {
      fields: [
          'title',
        {key: 'year', label: 'Production Year'},
          'cast',
          'genres'
      ],
      items: moviesList,
    };
  },
};
</script>

<style scoped>

</style>
