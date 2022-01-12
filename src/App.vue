<template>
  <div id="app">
    <Header  @researchDone="searchMoviesAndSeries" />
    <Main :moviesInfoArray="moviesArray" :seriesInfoArray="seriesArray" />
  </div>
</template>

<script>
import Header from "./components/Header.vue";
import Main from "./components/Main.vue";
import axios from 'axios';

export default {
  name: "App",
  components: {
    Header,
    Main
  },
  data:function(){
    return{
      searchedText: '',
      apiKey: '6defc1c860b27887bb893ddc9fb8fe05',
      moviesArray: [],
      seriesArray:[]
    }
  },
  methods:{
    searchMoviesAndSeries: function(searched){
      this.searchedText = searched;
      this.axiosMoviesCall();
      this.axiosSeriesCall();
    },
    // Calling the API for the movies
    axiosMoviesCall: function (){
      axios.get('https://api.themoviedb.org/3/search/movie', {
        params:{
          api_key: this.apiKey,
          query: this.searchedText
        }
      }).then((response) =>{
        this.moviesArray = response.data.results
      });
    },
    // Calling the API for the TV Series
    axiosSeriesCall: function (){
      axios.get('https://api.themoviedb.org/3/search/tv', {
        params:{
          api_key: this.apiKey,
          query: this.searchedText
        }
      }).then((response) =>{
        this.seriesArray = response.data.results
        console.log(this.seriesArray)
      });
    },

  }
};
</script>

<style lang="scss">
@import './style/general.scss';
</style>
