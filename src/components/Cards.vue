<script>    
export default{
    props:{
        card:{
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
    <li class="card">
        <p>{{ card.title }}</p>
        <p>{{ card.original_title }}</p>
        <p>{{ card.original_language }}</p>
        <p>{{ card.vote_average }}</p>
    </li>
</template>

<style scoped lang="scss">

</style>