<template>
  <ul class="list-group col-md-4">
    <VideoListItem
      v-for="video in videos"
      v-bind:video="video"
      v-bind:key="video.etag"
      v-on:videoSelect="onVideoSelect"
    >
    </VideoListItem>
  </ul>
</template>

<script>
import VideoListItem from "./VideoListItem";

export default {
  name: "VideoList",
  props: {
    videos: Array
  },
  components: {
    VideoListItem
  },
  methods: {
    onVideoSelect(video) {
      this.$emit("videoSelect", video);
    }
  }
};
</script>

<style scoped></style>
