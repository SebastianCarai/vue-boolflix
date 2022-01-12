<template>
    <main>
        <div class="my_container">
            <!-- Movies -->
            <div class="search_results">
                <h2>Films:</h2>
                <div class="d-flex flex-wrap justify-content-between">
                    <SingleCard v-for="(singleMovieCard, index) in moviesInfoArray" :key="index" :cardInfo="singleMovieCard" :variable="'title'"/>
                </div>
            </div>
            <!-- Tv series -->
            <div class="search_results">
                <h2>Series:</h2>
                <div class="d-flex flex-wrap justify-content-between">
                    <SingleCard v-for="(singleSeriesCard, index) in seriesInfoArray" :key="index" :cardInfo="singleSeriesCard" :variable="'name'"/>
                </div>
            </div>
        </div>
    </main>
</template>

<script>
import SingleCard from "./SingleCard.vue";

export default {
    name: "Main",
    components:{
        SingleCard,
    },
    props:{
        moviesInfoArray: Array,
        seriesInfoArray: Array
    }
}
</script>

<style scoped lang="scss">
main{
    height: calc(100vh - 80px);
    overflow-y: auto;
    .my_container{
        width: 95%;
        margin: auto;
        .search_results{
            margin-bottom: 30px;
            h2{
                color: white;
            }
        }
    }
}
</style>