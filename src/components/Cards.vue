<script>    
import {store} from '../store'
export default{
    props:{
        card:{
            type: Object
        },
    },

    data(){
        return{
            store,
            stars: [],
            flags: {
                it: '../assets/it.png',
                en: '../assets/gb-eng.png',
                de: '../assets/de.png',
                es: '../assets/es.png',
            }
        }
    },

    methods:{
        changeRangeVote(){
            const newValue = parseInt(this.card.vote_average * 0.5) 
            console.log(newValue)
            return newValue
        },
    },

    computed:{
        urlImg(){
            return 'https://image.tmdb.org/t/p/' + 'w500' + this.card.poster_path
        }
    }
}
</script>

<template>
    <li>
 
        <img class="card-img" :src="urlImg" alt="">
    
        <div class="card-description">
            <h1>{{ card.title !== undefined ? card.title : card.name }}</h1>
            <h3>{{ card.original_title !== undefined ? card.original_title : card.original_name }}</h3>       
            
            <img v-if="flags[card.original_language] !== undefined" :src="flags[card.original_language]" alt="">
            <p v-else>{{ card.original_language }}</p>
            
            <p> {{ changeRangeVote() }} 
                <i :class="changeRangeVote() === 1 || changeRangeVote() === 2 || changeRangeVote() === 3 || changeRangeVote() === 4 || changeRangeVote() === 5  ? 'active' : '' " class="fa-solid fa-star"></i> 
                <i :class="changeRangeVote() === 2 || changeRangeVote() === 3 || changeRangeVote() === 4 || changeRangeVote() === 5 ? 'active' : '' " class="fa-solid fa-star"></i>
                <i :class="changeRangeVote() === 3 || changeRangeVote() === 4 || changeRangeVote() === 5 ? 'active' : '' " class="fa-solid fa-star"></i>
                <i :class="changeRangeVote() === 4 || changeRangeVote() === 5 ? 'active' : '' " class="fa-solid fa-star"></i>
                <i :class="changeRangeVote() === 5 ? 'active' : '' " class="fa-solid fa-star"></i>
            </p>

            <p>{{ card.overview }}</p>
        </div>
        
    </li>

</template>

<style scoped lang="scss">
    .active{
        color: yellow;
    }

    .card-img{
        height: 750px;
        width: 500px;
    }

    .card-description{
        display: none;
    }
    li:hover .card-description{
        position: absolute;
        top: 0;
        left: 0;
        right: 0;
        bottom: 0;
        color: white;
        background-color: rgba($color: #000000, $alpha: 0.7);
        padding: 30px;
        display: block;
    }

    
</style>