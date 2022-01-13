<template>
    <div class="single_card">

        <div class="front_page" v-if="cardInfo.poster_path !== null">
            <img :src="`https://image.tmdb.org/t/p/w342${cardInfo.poster_path}`" alt="">
        </div>
        <h2 v-else class="front_page"> {{ cardInfo[variable] }} </h2>

        <div class="back_page">
            <div>
               <strong> Nome:</strong> {{cardInfo[variable]}}
            </div>

            <div>
                <strong>Nome originale: </strong> {{cardInfo['original_' + variable]}}
            </div>


            <div>
                <strong>Lingua</strong>:
                <span v-if="cardInfo.original_language == 'it' || cardInfo.original_language == 'en' || cardInfo.original_language == 'es'">
                    <img :src="require(`../assets/img/${cardInfo.original_language}.png`)" alt="" class="language_flag">
                </span> 
                <span v-else>
                    {{cardInfo.original_language}}
                </span>
            </div>

            <div>
                <strong>Voto: </strong>
                <i class="fas fa-star full_star" v-for="(star, index) in starVote" :key="index"></i>
                <i class="far fa-star" v-for="(empty, i) in (5 - starVote)" :key="i"></i>
            </div>

            <div>
                <strong>Overview: </strong> {{cardInfo.overview}}
            </div>
        </div>
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
    height: 507px;
    margin: 10px 0;
    border: 2px solid white;
    .front_page{
        height: 100%;
        width: 100%;
        img{
        height: 100%;
        width: 100%;
        object-fit: cover;
        }
    }
    h2.front_page{
        text-align: center;
        font-weight: bold;
    }
    .back_page{
        display: none;
        color: white;
        background-color: black;
        height: 100%;
        padding: 8px;
        .language_flag{
        width: 20px;
        position: relative;
        bottom: 1.5px;
        } 
        .full_star{
            color: orange;
        }
        div{
            font-size: 16px;
        }
    }
}
.single_card:hover .front_page{
    display: none;
}
.single_card:hover .back_page{
    display: block;
}
</style>