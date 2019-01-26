<template>
  <div>
		<h1 display-4 font-weight-bold >Find your movie...</h1>
		<div>
			<form class="search-form" @submit.prevent>
        <input 
          v-model="searchTitle"
          type="text" 
          class="SearchInput" 
          placeholder="Search by title.."
          v-on:keyup="(searchFilm(searchTitle))"
        >
       </form>

      <span v-if="error.length > 0"  class="error">
        {{error}}
      </span>
		</div>		 
  </div>
</template>

<script>
export default {
  name: 'Search',
  data() {
    return{
      searchTitle:'',
      error: ''
    }
  },
  methods:{
    searchFilm(searchTitle){
      this.$emit('searchFilm', searchTitle);
    }
  }
};
</script>

<style scoped>
  input {
    background: transparent;
    border: none;
    outline: none;
    font-size: 1.2em;
    color: #a03232;
    border-bottom: 1px solid #500505;
    margin: 1.2em;
  }
</style>
