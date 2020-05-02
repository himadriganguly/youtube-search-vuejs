<template>
  <div class="container">
    <img alt="Vue logo" src="./assets/logo.png" />
    <SearchBar v-on:termChange="onTermChange"></SearchBar>
    <div class="row">
      <VideoDetail v-bind:video="selectedVideo"></VideoDetail>
      <VideoList v-bind:videos="videos" v-on:videoSelect="onVideoSelect">
      </VideoList>
    </div>
  </div>
</template>

<script>
import axios from "axios";
import SearchBar from "./components/SearchBar.vue";
import VideoList from "./components/VideoList.vue";
import VideoDetail from "./components/VideoDetail.vue";

const API_KEY = "YOUR API KEY FOR YOUTUBE";

export default {
  name: "App",
  data: () => {
    return {
      videos: [],
      selectedVideo: null
    };
  },
  components: {
    SearchBar,
    VideoList,
    VideoDetail
  },
  methods: {
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
          this.videos = response.data.items;
          this.selectedVideo = this.videos[0];
        });
    },
    onVideoSelect(video) {
      this.selectedVideo = video;
    }
  }
};
</script>

<style scoped>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
div {
  text-align: center;
}
</style>
