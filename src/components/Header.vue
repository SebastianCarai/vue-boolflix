<template>
    <header class="d-flex align-items-center">
        <div>
            <input v-model="searchResult" type="text" placeholder="Cerca" class="m-1">
            <button @click="$emit('researchDone', searchResult)" class="btn btn-primary">Cerca</button>
        </div>
    </header>
</template>

<script>
export default {
    name: "Header",
    data: function (){
        return {
            searchResult: '',
        }
    }
}
</script>

<style scoped lang="scss">
header{
    height: 80px;
    background-color: black;
}
</style>