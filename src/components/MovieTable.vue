<template>
  <div class="overflow-auto">
    <b-table ref="moviesTable" condensed hover :items="items" :fields="fields" :per-page="perPage">
      <template #cell(title)="data">
        {{ data.item.title }}
      </template>
      <template #cell(year)="data">
        {{ data.item.year }}
      </template>
      <template #cell(cast)="data">
        <span v-for="(item, index) in data.item.cast" v-bind:key="index">
          {{ item }}<span v-if="index !== data.item.cast.length - 1">,</span>
        </span>
      </template>
      <template #cell(genres)="data">
        <span v-for="(item, index) in data.item.genres" v-bind:key="index">
          {{ item }}<span v-if="index !== data.item.genres.length - 1">,</span>
        </span>
      </template>
    </b-table>
    <b-button id="showMore" block variant="info" @click="showMoreElements">Show more</b-button>
  </div>
</template>

<script>
import movies from "../assets/movies/movies.json";
import {EventBus} from "@/event-bus";
import {_} from 'vue-underscore';

export default {
  name: "MovieTable",
  data() {
    return {
      perPage: 10,
      fields: [
        "title",
        {key: "year", label: "Production Year"},
        "cast",
        "genres",
      ],
      items: movies,
    };
  },
  methods: {
    showMoreElements() {
      this.perPage += 10
    },
    filterMovies(form) {
      return _.filter(movies, function (item) {
        if (form.title !== '' && !item.title.toLowerCase().includes(form.title.toLowerCase()))
          return false
        if (form.productionYearFrom !== '' && item.year < form.productionYearFrom)
          return false
        if (form.productionYearTo !== '' && item.year > form.productionYearTo)
          return false
        return !(form.cast !== '' && !_.contains(item.cast, form.cast))
        /*if(form.cast !== '' && !item.cast.toString().toLowerCase().includes(form.cast.toLowerCase()))
          return false
        return true*/
      })
    }
  },
  mounted() {
    EventBus.$on('search-value', (value) => {
      this.items = this.filterMovies(value)
    });
  }
};
</script>

<style scoped>
</style>
