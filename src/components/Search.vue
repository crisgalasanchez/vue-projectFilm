<template>
  <div>
		<h1 display-4 font-weight-bold >Find your movie...</h1>
    <v-layout justify-center>
      <v-flex xs10 sm6>
        <v-form ref="form">
          <v-text-field
            v-model="searchTitle"
            label="Search by title.."
            clearable
            color="blue-grey darken-2"
            v-on:keyup="(searchFilm(searchTitle))"
            @click:clear="(clearSearch())"
          ></v-text-field>
        </v-form>
          
        <span v-if="error.length > 0"  class="error">
          {{this._props.error}}
        </span>
      </v-flex>	
    </v-layout> 
  </div>
</template>

<script>
export default {
  name: 'Search',
  props: {
    error: {
        type: String
    }
  },
  data() {
    return{
      searchTitle:''
    }
  },
  methods:{
    searchFilm(searchTitle){
      this.$emit('searchFilm', searchTitle);
    },
    clearSearch(){
      this.$emit('clearSearch');
    }
  }
};
</script>

<style scoped>
</style>
