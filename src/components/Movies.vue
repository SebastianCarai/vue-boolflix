<template>
    <main>
        <div class="d-flex flex-wrap">
            <div class="row row-cols-4">
                <SingleCard v-for="(singleCard, index) in infoArray" :key="index" :cardInfo="singleCard"/>
            </div>
        </div>
    </main>
</template>

<script>
import SingleCard from "./SingleCard.vue";

export default {
    name: "Movies",
    components:{
        SingleCard
    },
    props:{
        infoArray: Array
    }
}
</script>

<style scoped lang="scss">
main{
    height: calc(100vh - 80px);
    overflow-y: auto;
}
</style>