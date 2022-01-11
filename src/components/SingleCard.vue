<template>
    <div class="single_card">
        <ul>
            <li>
                {{cardInfo.title}}
            </li>
            <li>
                {{cardInfo.original_title}}
            </li>
            <li>
                {{cardInfo.original_language}}
            </li>
            <li>
                {{cardInfo.vote_average}}
            </li>
        </ul>
    </div>
</template>

<script>
export default {
    name: "SingleCard",
    props:{
        cardInfo: Object
    }
}
</script>

<style lang="scss" scoped>
.single_card{
    border: 1px solid black;
    padding: 10px;
}
</style>