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
    <li>
        <p>{{ card.title }}</p>
    </li>
</template>

<style>
</style>