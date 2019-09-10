<template>
  <div v-if="video" class="col-md-8">
    <div class="embed-responsive embed-responsive-16by9">
      <iframe :src="videoUrl" class="embed-responsive-item"></iframe>
    </div>
    <div class="details">
      <h4>{{video.snippet.title}}</h4>
      <p>{{video.snippet.description}}</p>
    </div>
  </div>
</template>    

<script>
import videoListItem from "./videoListItem";

export default {
  name: "videoDetail",
  props: ["video"],
  //   components: {
  //     videoListItem
  //   }
  computed: {
    videoUrl() {
      const { videoId } = this.video.id;
      return `https://www.youtube.com/embed/${videoId}`;
    }
  }
};
</script>
 
<style  scoped>
.details {
  margin-top: 1em;
  padding: 1em;
  border: 1px solid #ddd;
  border-radius: 0.4em;
}
</style>