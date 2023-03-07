<script>
import {store} from '../store'
export default{
    data(){
        return{
            store
        }
    }
}
</script>

<template>
    <header>
        <input class="search-bar" type="text" v-model="store.searchMovie">
    </header>
</template>

<style scoped lang="scss">
    header{
        padding: 10px;
        background-color: black;
        text-align: center;

        .search-bar{
            padding: 10px;
        }
    }
</style>