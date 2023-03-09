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
            <ul class="option">
                <li>Home</li>
                <li>Serie TV</li>
                <li>Film</li>
                <li>Originali</li>
                <li>Aggiunti di recente</li>
                <li>La mia lista</li>
            </ul>
        </div>
        <div class="input">
            <input class="search-bar" type="text" @keyup.enter="setSearch" v-model="localSearch" placeholder="Titoli...">
            <span class="button" @click="setSearch"><i class="fa-solid fa-magnifying-glass"></i></span>
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
        background-color: black;
        border-color: white;
        color: white;
    }

    .button{
        padding: 10px;
        color: white;
    }
    .logo {

        display: flex;
        align-items: center;
        gap: 20px;

        img{
            width: 150px;
        }
    }

    .option{
        display: flex;
        gap: 15px;
        color: white;
        font-size: 14px;
    }

    .input{
        display: flex;
        align-items: center;
    }
</style>