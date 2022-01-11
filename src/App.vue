<template>
  <div id="app">
    <Header  @researchDone="axiosCall" />
    <Movies :infoArray="responseArray" />
  </div>
</template>

<script>
import Header from "./components/Header.vue";
import Movies from "./components/Movies.vue";
import axios from 'axios';

export default {
  name: "App",
  components: {
    Header,
    Movies
  },
  data:function(){
    return{
      searchedText: '',
      responseArray: []
    }
  },
  methods:{
    // Calling the API and pushing the results into the responseArray array
    axiosCall: function (text){
      this.searchedText = text
      axios.get('https://api.themoviedb.org/3/search/movie', {
        params:{
          api_key: "6defc1c860b27887bb893ddc9fb8fe05",
          query: this.searchedText
        }
      }).then((response) =>{
        this.responseArray = response.data.results
        console.log(this.responseArray)
      });
    }
  }
};
</script>

<style lang="scss">
@import './style/general.scss';
</style>
