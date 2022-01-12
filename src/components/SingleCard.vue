<template>
    <div class="single_card">
        <ul>
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
                Voto: {{cardInfo.vote_average}}
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
            // flag
        }
    }
}
</script>

<style lang="scss" scoped>
.single_card{
    border: 1px solid black;
    padding: 10px;
    .language_flag{
        width: 20px;
        position: relative;
        bottom: 1.5px;
    }
    .england_flag{
    border: 1px solid black;
    }  
}
</style>