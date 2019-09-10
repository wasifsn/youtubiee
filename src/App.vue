<template>
  <div class="container">
    <searchBar @termChange="onTermChange"></searchBar>
    <div class="row">
      <videoDetail :video="selectedVideo" />
      <videoList @videoSel="onVideoSelect" :videos="videos"></videoList>
    </div>
  </div>
</template>

<script>
import axios from "axios";
import searchBar from "./components/searchBar";
import videoDetail from "./components/videoDetail";
import videoList from "./components/videoList";
import videoListItem from "./components/videoListItem";

const API_KEY = "AIzaSyCDg6-ANdMNjqv39qd7QJzQiTJrTs3iiO0";
export default {
  name: "App",
  components: {
    searchBar,
    videoDetail,
    videoList,
    videoListItem
  },
  data: function() {
    return {
      videos: [],
      selectedVideo: null
    };
  },
  methods: {
    onVideoSelect(video) {
      this.selectedVideo = video;
      console.log(video);
    },
    onTermChange(searchTerm) {
      axios
        .get("https://www.googleapis.com/youtube/v3/search", {
          params: {
            key: API_KEY,
            type: "video",
            part: "snippet",
            q: searchTerm
          }
        })
        .then(response => {
          console.log(response.data);
          this.videos = response.data.items;
          console.log(this.videos);
        });
    }
  }
};
</script>

<style scoped>
</style>