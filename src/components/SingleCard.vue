<template>
    <div class="single_card">
        <ul>
            <li>
                <img :src="`https://image.tmdb.org/t/p/w342${cardInfo.poster_path}`" alt="">
            </li>
            <li>
                Nome: {{cardInfo[variable]}}
            </li>
            <li>
                Nome originale: {{cardInfo['original_' + variable]}}
            </li>
            <li>
                Lingua:
                <span v-if="cardInfo.original_language == 'it' || cardInfo.original_language == 'en' || cardInfo.original_language == 'es'">
                    <img :src="require(`../assets/img/${cardInfo.original_language}.png`)" alt="" class="language_flag">
                </span> 
                <span v-else>
                    {{cardInfo.original_language}}
                </span>
            </li>
            <li>
                Voto: 
                <i class="fas fa-star full_star" v-for="(star, index) in starVote" :key="index"></i>
                <i class="far fa-star" v-for="(empty, i) in (5 - starVote)" :key="i"></i>
            </li>
        </ul>
    </div>
</template>

<script>
export default {
    name: "SingleCard",
    props:{
        cardInfo: Object,

        // Poichè la key "nome" e "nome originale" varia in base a se ho un film (title e original_title)
        // o una serie TV (name e orginal_name), con questa variabile ho la possibilità, attraverso un prop, di passare il nome della chiave
        variable: String
    },
    data: function(){
        return{
            starVote: parseInt(Math.round(this.cardInfo.vote_average / 2)),
        }
    }
}
</script>

<style lang="scss" scoped>
@import '../style/general.scss';

.single_card{
    border: 1px solid black;
    background-color: white;
    width: 342px;
    margin: 10px 0;
    img{
        width: 100%;
    }
    .language_flag{
        width: 20px;
        position: relative;
        bottom: 1.5px;
    } 
    .full_star{
        color: orange;
    }
}
</style>