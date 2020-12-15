<template>
  <b-form v-if="show">
    <b-form-group
      id="input-group-1"
      label="Tytuł"
      label-for="inputTitle">
      <b-form-input
        id="inputTitle"
        v-model="form.title"
        type="text"
        placeholder="Podaj tytuł lub fragment tytułu filmu">
      </b-form-input>
    </b-form-group>
    <b-form-group
      id="input-group-2"
      label="Rok produkcji od:"
      label-for="inputProductionYearFrom"
      label-cols-sm="4"
    >
      <b-form-input
        id="inputProductionYearFrom"
        v-model="form.productionYearFrom"
        type="text"
        placeholder="Liczba naturalna z przedziału 1900-2019">
      </b-form-input>
    </b-form-group>
    <b-form-group
        id="input-group-3"
        label="Rok produkcji do:"
        label-for="inputProductionYearTo"
        label-cols-sm="4"
    >
      <b-form-input
          id="inputProductionYearTo"
          v-model="form.productionYearTo"
          type="text"
          placeholder="Liczba naturalna z przedziału 1900-2019">
      </b-form-input>
    </b-form-group>
    <b-form-group
      id="input-group-4"
      label="Obsada"
      label-for="inputCast">
      <b-form-input
        id="inputCast"
        v-model="form.cast"
        type="text"
        placeholder="Imię i nazwisko">
      </b-form-input>
    </b-form-group>
    <b-button id='searchButton' variant="info col-sm-12" type="button" @click="emitSearch">Szukaj</b-button>
  </b-form>
</template>

<script>
import {EventBus} from "@/event-bus";

export default {
  name: 'SearchEngine',
  data() {
    return {
      form: {
        title: '',
        productionYearFrom: '',
        productionYearTo: '',
        cast: ''
      },
      show: true
    }
  },
  methods:{
    emitSearch() {
      EventBus.$emit('search-value',this.form)
    }
  },

}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
