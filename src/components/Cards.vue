<script>    
export default{
    props:{
        cardMovie:{
            type: Object
        },

        cardSeries:{
            type: Object
        }
    },

    data(){
        return{

        }
    }
}
</script>

<template>
    <li>
        <p>{{ cardMovie.title }}</p>
        <p>{{ cardMovie.original_title }}</p>

        <div v-if="cardMovie.original_language === 'en'">
            <img src="../assets/gb-eng.png" alt="">
        </div>
        <div v-else-if="cardMovie.original_language === 'it'">
            <img src="../assets/it.png" alt="">
        </div>
        <div v-else-if="cardMovie.original_language === 'de'">
            <img src="../assets/de.png" alt="">
        </div>
        <div v-else-if="cardMovie.original_language === 'es'">
            <img src="../assets/es.png" alt="">
        </div>
        <div v-else>
            <p>{{ cardMovie.original_language }}</p>
        </div>

        <p>{{ cardMovie.vote_average }}</p>
    </li>

    <li>
        <p>{{ cardSeries.name }}</p>
        <p>{{ cardSeries.original_name }}</p>

        <div v-if="cardSeries.original_language === 'en'">
            <img src="../assets/gb-eng.png" alt="">
        </div>
        <div v-else-if="cardSeries.original_language === 'it'">
            <img src="../assets/it.png" alt="">
        </div>
        <div v-else-if="cardSeries.original_language === 'de'">
            <img src="../assets/de.png" alt="">
        </div>
        <div v-else-if="cardSeries.original_language === 'es'">
            <img src="../assets/es.png" alt="">
        </div>
        <div v-else>
            <p>{{ cardSeries.original_language }}</p>
        </div>

        <p>{{ cardSeries.vote_average }}</p>
    </li>

</template>

<style scoped lang="scss">

</style>