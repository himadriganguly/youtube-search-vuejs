<template>
  <li class="list-group-item media" v-on:click="onVideoSelect">
    <img class="mr-3" v-bind:src="thumbnailUrl" alt="" />
    <div class="media-body">
      {{ video.snippet.title }}
    </div>
  </li>
</template>

<script>
export default {
  name: "VideoListItem",
  props: {
    video: Object
  },
  computed: {
    thumbnailUrl() {
      return this.video.snippet.thumbnails.default.url;
    }
  },
  methods: {
    onVideoSelect() {
      this.$emit("videoSelect", this.video);
    }
  }
};
</script>

<style scoped>
li {
  -ms-text-align-last: left;
  text-align-last: left;
  float: left;
  cursor: pointer;
}
li:hover {
  background-color: #eee;
}
img {
  margin-right: 20px;
  float: left;
}
</style>
