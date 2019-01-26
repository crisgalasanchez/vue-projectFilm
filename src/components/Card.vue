<template>
    <v-card mx-auto weight="200px">
        <v-img :src="existsPoster(film.Poster)">
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
                depressed>
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
    methods: {
        existsPoster(poster){
            if(poster === 'N/A'){
                return 'https://www.classicposters.com/images/nopicture.gif';
            }else{
                return poster;
            }
        }
    }
};
</script>

<style scoped>
</style>