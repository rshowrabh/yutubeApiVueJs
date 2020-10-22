<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <div class="container">
      <div class="row">
        <div class="col-12 py-3"> <searchBar @termChange='termChange'/></div>
        <div class="col-8">  <videoDetail :video='selectVideo'/></div>
        <div class="col-4"><videoList @videoSelect='onVideoSelect' :videos="videos"></videoList> </div>
      </div>
    </div>
   
  </div>
</template>

<script>
import axios from 'axios';
import searchBar from './components/searchBar.vue';
import videoList from './components/videoList.vue';
import videoDetail from './components/videoDetail.vue';

const API_KEY = 'AIzaSyDLzzloDYDaeRxQIJ8RynQNjnstxjl3aQc';

export default {
  name: 'App',
  data(){
    return {
      videos: [],
      selectVideo: null,
    }
  },
  methods: {
    onVideoSelect(video){
     this.selectVideo = video;
    },
    termChange: function(e){
      axios.get('https://www.googleapis.com/youtube/v3/search',{
        params : {
        key: API_KEY,
        type:'video',
        part:'snippet',
        q:e,
        }

      }).then(response => {
        this.videos = response.data.items
        console.log(response)
      })
    }
  },
  components: {
    searchBar,
    videoList,
    videoDetail,
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
