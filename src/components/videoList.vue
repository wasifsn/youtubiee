<template>
  <ul class="list-group col-md-4">
    <videoListItem
      v-for="video in videos"
      :video="video"
      :key="video.etag"
      @videoSel="onVideoSelect"
    ></videoListItem>
  </ul>
</template>    

<script>
import videoListItem from "./videoListItem";

export default {
  name: "videoList",
  props: { videos: Array },
  components: {
    videoListItem
  },
  methods: {
    onVideoSelect(video) {
      this.$emit("videoSel", video);
    }
  }
};
</script>
 
<style  scoped>
</style>