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
            store,
        }
    },

    computed:{
        search(){
            return this.store.searchMovie
        },
    },

    watch:{
        search(newValue, oldValue){
            console.log(oldValue, newValue)
            this.fetchCards()
        },
    },

    methods:{
        fetchCards(){
            this.fetchMovies()
            this.fetchSeries()
        },

        fetchMovies(){
            
            axios.get('https://api.themoviedb.org/3/search/movie?api_key=3df3427edaf72e4e9aac84491c75f583', {
                params:{
                    query: this.search,
                    language: 'it-IT'
                }
            })
            .then((res) => {
                this.store.movieCards = res.data.results
                console.log(this.store.movieCards)
            }).catch(()=>{
                this.store.movieCards = []
            })
        },

        fetchSeries(){
            
            axios.get('https://api.themoviedb.org/3/search/tv?api_key=3df3427edaf72e4e9aac84491c75f583', {
                params:{
                    query: this.search,
                    language: 'it-IT'
                }
            })
            .then((res) => {
                this.store.tv = res.data.results
                console.log(this.store.tv)
            }).catch(()=>{
                this.store.tv = []
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
        <div>
            <h1 class="title">Film</h1>
            <ul class="list-card">
                <Cards class="card-item" v-for="el in store.movieCards" :card="el"/>
            </ul>

            <h1 class="title">Serie Tv</h1>
            <ul class="list-card">
                <Cards class="card-item" v-for="el in store.tv" :card="el"/>
            </ul>
        </div>
    </main>
</template>

<style lang="scss" scoped>
@use '../style/partials/variables.scss';

.list-card{
    display: flex;
    white-space: nowrap;
    overflow: auto;
    padding: 0 30px;
    
    .card-item{
        width: 500px;
        position: relative;
    }
}

.title{
    padding: 30px;
    color: white;
    text-transform: uppercase;
    font-size: 35px;
    font-weight: 600;
}
</style>