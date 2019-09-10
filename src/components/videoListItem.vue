<template>
  <div>
    <li @click="onVideoSelect" class="list-group-item media">
      <img class="mr-3" :src="thumbnailUrl" />
      <div class="media-body">{{video.snippet.title}}</div>
    </li>
  </div>
</template>    
<script>
export default {
  name: "videoListItem",
  props: ["video"],
  computed: {
    thumbnailUrl() {
      return this.video.snippet.thumbnails.default.url;
    }
  },
  methods: {
    onVideoSelect() {
      this.$emit("videoSel", this.video);
    }
  }
};
</script>
 
<style  scoped>
li {
  display: flex;
  align-items: center;
  cursor: pointer;
}

li:hover {
  background-color: #eee;
}
</style> 