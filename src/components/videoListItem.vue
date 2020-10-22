<template>

    <li class="media" @click="onVideoClick">
    <img  :src="thumbnaiUrl" class="mr-3"  alt="Generic placeholder image">
    <div class="media-body">
      <h5 class="mt-0 mb-1">{{video.snippet.title}}</h5>
        
    </div>
    <hr>
  </li>
  
  
</template>

<script>
export default {
    name: 'videoListItem',
    props: ['video'],
    methods: {
        onVideoClick(){
            this.$emit('videoSelect', this.video)
        }
    },
    computed: {
        thumbnaiUrl(){
            return this.video.snippet.thumbnails.default.url
        }
    }

}
</script>

<style>

</style>