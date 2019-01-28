<template>
  <v-container grid-list-md fluid>
    <v-layout wrap justify-space-around>
      <v-flex xs12 sm6 md4 pa-4 v-for="film in listFilms" :key="film.id">
        <Card v-bind:film="film" v-bind:listFilms="listFilms"/>
      </v-flex>
    </v-layout>
  </v-container>
</template>

<script>
import Card from '@/components/Card.vue'

export default {
  name: 'FilmList',
  components: {
    Card
  },
  props: {
    listFilms: {
      type: Array
    }
  }
}
</script>

<style scoped>
</style>
