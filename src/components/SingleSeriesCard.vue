<template>
    <div class="single_series_card">
        <ul>
            <li>
                {{seriesInfo.name}}
            </li>
            <li>
                {{seriesInfo.original_name}}
            </li>
            <li>
                {{seriesInfo.original_language}}
            </li>
            <li>
                {{seriesInfo.vote_average}}
            </li>
        </ul>
    </div>
</template>

<script>
export default {
    name: "SingleSeriesCard",
    props:{
        seriesInfo: Object
    }
}
</script>

<style lang="scss" scoped>
.single_series_card{
    border: 1px solid blue;
    padding: 10px;
}
</style>