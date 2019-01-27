<template>
    <v-flex xs12>
        <v-card color="blue-grey darken-2" class="white--text">
            <v-layout>
                <v-flex xs4 pa-3>
                    <v-img
                        :src="filmInfo.Poster"
                        height="250px"
                        contain>
                    </v-img>
                </v-flex>
                <v-flex xs7>
                    <v-card-title primary-title>
                        <div>
                            <h4 class="display-1">{{filmInfo.Title}}</h4>
                            <h5 class="pa-3">DIRECTOR: {{filmInfo.Director}} {{filmInfo.Year}}</h5>
                            <p>{{filmInfo.Plot}}</p>
                        </div>
                    </v-card-title>
                </v-flex>
            </v-layout>
            <v-divider light></v-divider>
            <v-card-actions class="info-card">
                ✪ Rating: {{filmInfo.imdbRating}}
                <v-btn v-on:click="backToFilms" flat dark>Back to films</v-btn>
            </v-card-actions>
        </v-card>
    </v-flex>
</template>

<script>
export default {
    name: 'Info',
    data(){
        return {
            filmInfo : {}
        }
    },
    mounted(){
        const URL = 'https://www.omdbapi.com/?apikey=f12ba140&i=' + this.$route.params.id;
        fetch(URL)
        .then(response => response.json())
        .then(json => {
            this.filmInfo=json
        });
    },
    methods:{
        backToFilms(){
            this.$router.go(-1)
        }
    }
}
</script>

<style>
.info-card {
  display: flex;
  justify-content: space-around;
  margin:10px 20px;
}
</style>

