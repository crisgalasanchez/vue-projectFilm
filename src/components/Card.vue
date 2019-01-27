<template>
    <v-card mx-auto weight="200px">
        <v-img :src="existsPoster">
        <v-layout
            align-end
            fill-height
            pa-3
            white--text >
        </v-layout>
        </v-img>
        <v-card-title>
            <div text-truncate>{{ film.Title }}</div>
        </v-card-title>
        <v-divider></v-divider>
        <v-card-actions>
            <v-spacer></v-spacer>
            <v-btn
                color="red"
                dark
                depressed
                v-on:click="showInfo">
                More info
            </v-btn>
        </v-card-actions>
    </v-card>
</template>

<script>
export default {
	name: 'Card',
    props: {
        film: {
            type: Object
        }
    },
    computed: {
        existsPoster: function () {
            return (this._props.film.Poster === 'N/A')
                ? 'https://www.classicposters.com/images/nopicture.gif'
                : this._props.film.Poster ;
        }
    },
    methods: {
        showInfo(){
            this.$router.push('/'+this._props.film.imdbID);
        }
    }
};
</script>

<style scoped>
</style>