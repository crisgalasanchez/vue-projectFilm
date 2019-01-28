<template>
    <div>
        <Search
          v-on:searchFilm="searchFilm"
          v-on:clearSearch="clearSearch"
          v-bind:error="error"/>
        <FilmList v-bind:listFilms="listFilms"/>
    </div>
</template>

<script>
import axios from 'axios'
import Search from '@/components/Search.vue'
import FilmList from '@/components/FilmList.vue'

export default {
  name: 'Home',
  components: {
    Search,
    FilmList
  },
  data () {
    return {
      listFilms: [],
      searchTitle: '',
      error: ''
    }
  },
  methods: {
    searchFilm (searchTitle) {
      if (this.validateForm(searchTitle)) {
        this.callApi(searchTitle)
      } else {
        this.listFilms = []
      }
    },
    validateForm (searchTitle) {
      return searchTitle != null && searchTitle.length > 0
    },
    callApi (searchTitle) {
      let url = 'https://www.omdbapi.com/?apikey=f12ba140&s='
      url += searchTitle
      axios
        .get(url)
        .then(response => {
          this.listFilms = response.data.Search
        })
        .catch(error => {
          console.log(error)
          this.error = 'We are having problems. Try again later'
        })
    },
    clearSearch () {
      this.listFilms = []
    }
  }
}
</script>
