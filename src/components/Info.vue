<template>
    <div class="container__data">
        <div class="container__data--card d-flex flex-column">
            <h3 class="card-title">{{filmInfo.Title}} ({{filmInfo.Year}})</h3>
            <div class="d-flex flex-column flex-md-row">
                <div class="p-2">
                        <v-img :src="filmInfo.Poster"/>
                    <h6 class="font-weight-bold text-center pt-2">✪ Rating: {{filmInfo.imdbRating}}</h6>
                </div>
                <div class="p-2">
                    <ul class="d-flex flex-column">
                        <li class="d-flex justify-content">
                            <h5 class="mr-2">Director: </h5>
                            <p class="font-italic"> {{filmInfo.Director}}</p>
                        </li>
                        <li class="d-flex justify-content">
                            <h5 class="mr-2">Actors: </h5>
                            <p class="font-italic"> {{filmInfo.Actors}}</p>
                        </li >
                        <li class="d-flex justify-content">
                            <h5 class="mr-2">Duration: </h5>
                            <p class="font-italic"> {{filmInfo.Runtime}}</p>
                        </li >
                        <li class="d-flex justify-content">
                            <h5 class="mr-2">Language: </h5>
                            <p class="font-italic"> {{filmInfo.Language}}</p>
                        </li>
                        <li class="d-flex justify-content">
                            <h5 class="mr-2">Genre: </h5>
                            <p class="font-italic"> {{filmInfo.Genre}}</p>
                        </li>
                    </ul>
                </div>
            </div>
            <div class="card-body card__plot">
                <h2 class="card-subtitle pb-2">Plot</h2>
                <p class="card-text text-justify">{{filmInfo.Plot}}</p>
            </div>
            <div class="d-flex justify-content-around align-items-center">
                <button v-on:click="backToFilms" class="btn btn-dark">Back to films</button>
                <a title="filmInfo.Title" href="filmInfo.Website" about="_blank" alt= "Watch movie"><img class="icon__film" src={PlayFilm} alt="Watch video" /></a>
            </div>
        </div> 
    </div>
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
            this.$router.push('/');
        }
    }
}
</script>

<style>

</style>

