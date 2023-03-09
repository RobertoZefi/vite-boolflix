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
            return 'https://image.tmdb.org/t/p/' + 'w342' + this.card.backdrop_path
        }
    }
}
</script>

<template>
    <li>
        
            <img :src="urlImg" alt="">
    
            <h3>{{ card.title !== undefined ? card.title : card.name }}</h3>
            <h4>{{ card.original_title !== undefined ? card.original_title : card.original_name }}</h4>       
    
            <img v-if="flags[card.original_language] !== undefined" :src="flags[card.original_language]" alt="">
            <p v-else>{{ card.original_language }}</p>
    
    
            <p> {{ changeRangeVote() }} 
                <i :class="changeRangeVote() === 1 || changeRangeVote() === 2 || changeRangeVote() === 3 || changeRangeVote() === 4 || changeRangeVote() === 5  ? 'active' : '' " class="fa-solid fa-star"></i> 
                <i :class="changeRangeVote() === 2 || changeRangeVote() === 3 || changeRangeVote() === 4 || changeRangeVote() === 5 ? 'active' : '' " class="fa-solid fa-star"></i>
                <i :class="changeRangeVote() === 3 || changeRangeVote() === 4 || changeRangeVote() === 5 ? 'active' : '' " class="fa-solid fa-star"></i>
                <i :class="changeRangeVote() === 4 || changeRangeVote() === 5 ? 'active' : '' " class="fa-solid fa-star"></i>
                <i :class="changeRangeVote() === 5 ? 'active' : '' " class="fa-solid fa-star"></i>
            </p>
       

    </li>

</template>

<style scoped lang="scss">
    .active{
        color: yellow;
    }
</style>