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
        movie(){
            return this.store.searchMovie
        }
    },

    watch:{
        movie(newValue, oldValue){
            console.log(oldValue, newValue)
            this.fetchCards()
        }
    },

    methods:{
        fetchCards(){
            const searchValue = this.movie
            axios.get('https://api.themoviedb.org/3/search/movie?api_key=3df3427edaf72e4e9aac84491c75f583', {
                params:{
                    query: searchValue
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
            <ul class="list-card">
                <Cards v-for="movie in store.movieCards" :card="movie"/>
            </ul>
        </div>
    </main>
</template>

<style lang="scss" scoped>
@use '../style/partials/variables.scss';
.list-card{
    display: flex;
    gap: 50px;
    flex-wrap: wrap;
}
</style>