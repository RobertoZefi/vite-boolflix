<script>
import {store} from '../store'
export default{
    data(){
        return{
            store,
            localSearch: '',
        }
    }, 

    methods:{
        setSearch(){
            this.store.searchMovie = this.localSearch 
        }
    }
}
</script>

<template>
    <header>
        <div class="logo">
            <img src="/logo.png" alt="">
        </div>
        <div>
            <input class="search-bar" type="text" @keyup.enter="setSearch" v-model="localSearch" placeholder="Cerca...">
            <button class="button" @click="setSearch">Invio</button>
        </div>
    </header>
</template>

<style scoped lang="scss">
    header{
        padding: 10px;
        background-color: black;
        text-align: center;
        display: flex;
        align-items: center;
        justify-content: space-between;
    }

    .search-bar{
        padding: 10px;
    }

    .button{
        padding: 10px;
        background-color: white;
    }
    .logo {
        img{
            width: 150px;
        }
    }
</style>