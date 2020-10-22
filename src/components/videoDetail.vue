<template>
    <div v-if="video">

       <iframe width="560" height="315" :src="videoUrl" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
       <br>
       <h2> {{video.snippet.title}}</h2>
       <p> {{video.snippet.description}}</p>
    </div>
</template>

<script>
export default {
    name:'videoDetail',
    props: ['video'],
    computed: {
        videoUrl(){
            const videoId = this.video.id.videoId;
            return 'https://youtube.com/embed/'+ videoId;
        }
    }


}
</script>

<style>

</style>