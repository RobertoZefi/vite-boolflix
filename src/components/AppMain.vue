<script>
import axios from 'axios'
import {store} from '../store'
import Cards from './Cards.vue'
export default{
    components:{
        Cards
    },

    data(){
        return{
            store
        }
    },

    computed:{
        movies(){
            return this.store.movieCards
        }
    },

    methods:{
        fetchCards(){
            axios.get('https://api.themoviedb.org/3/search/movie?api_key=3df3427edaf72e4e9aac84491c75f583', {
                params:{
                    
                }
            })
            .then((res) => {
                this.store.movieCards = res.data.results
                console.log(this.store.movieCards)
            })
        }
    },

    created(){
        this.fetchCards()
    }
}
</script>

<template>
    <main>
        <div class="container">
            <ul>
                <Cards v-for="movie in store.movieCards" :card="movie"/>
            </ul>
        </div>
    </main>
</template>

<style lang="scss" scoped>
@use '../style/partials/variables.scss';


</style>