<template>
    <div>
        <Search v-on:searchFilm="searchFilm"/>
        <FilmList v-bind:listFilms="listFilms"/>
    </div>
</template>

<script>
import axios from 'axios'
import Search from '../components/Search.vue'
import FilmList from '../components/FilmList.vue'

export default {
  name: 'Home',
  components: {
    Search,
    FilmList
  },
  data() {
    return{
      listFilms :[],
      searchTitle:'',
      error: ''
    }
  },
  methods: {
    searchFilm(searchTitle){
      this.error = '';
      if(this.validateForm(searchTitle)){
        let listfilms = this.callApi(searchTitle);
      }else{
        this.error = 'Introduce a title'
      }
    },
    validateForm(searchTitle){
      return searchTitle.length > 0;
    },
    callApi(searchTitle){
      let url = 'https://www.omdbapi.com/?apikey=f12ba140&s=';
      url += searchTitle;
      
      axios
      .get(url)
      .then(response => {
        this.listFilms = response.data.Search
      })
      .catch(error => {
        console.log(error)
        this.error = 'Were having problems. Try again later'
      })
    }
  }
};
</script>