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
            
            
        }
    },

    methods:{
        changeRangeVote(){
            const newValue = parseInt(this.card.vote_average * 0.5) 
            console.log(newValue)
            return newValue
        },

        addStar(){
            for(let i = 0; i < this.changeRangeVote(); i++){
                this.stars.push('*')
            }
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
    
            <div v-if="card.title == null">
                <p>{{ card.name }}</p>
            </div>
            <div v-else>
                <p>{{ card.title }}</p>
            </div>
            
    
            <div v-if="card.original_title == null">
                <p>{{ card.original_name }}</p>
            </div>
            <div v-else>
                <p>{{ card.original_title }}</p>
            </div>
            
    
            <div v-if="card.original_language === 'en'">
                <img src="../assets/gb-eng.png" alt="">
            </div>
            <div v-else-if="card.original_language === 'it'">
                <img src="../assets/it.png" alt="">
            </div>
            <div v-else-if="card.original_language === 'de'">
                <img src="../assets/de.png" alt="">
            </div>
            <div v-else-if="card.original_language === 'es'">
                <img src="../assets/es.png" alt="">
            </div>
            <div v-else>
                <p>{{ card.original_language }}</p>
            </div>
    
    
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