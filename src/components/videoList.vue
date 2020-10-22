<template>
<div class="">
    <h1>Video List</h1>

    <ul class="list-unstyled">
    <videoListItem
         v-for="video in videos" :key="video.etag"
         :video='video'
         @videoSelect='onVideoSelect'
      ></videoListItem>
  
</ul>
</div>
   
</template>

<script>
import videoListItem from './videoListItem.vue';

export default {
    props: [
        'videos'
        ],
    name:'videoList',
    methods: {
        onVideoSelect(video){
            this.$emit('videoSelect', video)
        }
    },
    components: {
        videoListItem
    }
}
</script>