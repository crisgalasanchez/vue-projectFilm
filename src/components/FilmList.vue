<template>
  <v-container grid-list-md fluid>
    <v-layout wrap justify-space-around>
      <v-flex xs12 sm6 md4 pa-4 v-for="film in listFilms" :key="film.id">
        <Card v-bind:film="film"/>
      </v-flex>
    </v-layout>
  </v-container>
</template> 

<script>
import Card from '../components/Card.vue';

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
};
 /* data() {
    return {
      listFilms: listFilms,
    };
  },
     mounted () {
    axios
      .get('https://api.coindesk.com/v1/bpi/currentprice.json')
      .then(response => {
        this.info = response.data.bpi
      })
      .catch(error => {
        console.log(error)
        this.errored = true
      })
      .finally(() => this.loading = false)
  } */
</script>

<style scoped>
</style>