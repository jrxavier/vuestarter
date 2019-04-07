<template>
    <ul class="list-group">
        <VideoListItem 
            v-for="videoItem in videos"
            :video="videoItem"
            :key="videoItem.etag"   
            @videoSelect="onVideoSelect" 
            >
        </VideoListItem>    <!-- o evento videoSelect é captudado do componenet filho e repassado para cima-->
    </ul>
    <!-- Key - identificador unico do item que esta sendo trabalhado no v-on -->
</template>

<script>
import VideoListItem from './VideoListItem'

export default {
    name: 'VideoList',
    components: {
        VideoListItem
    },
    props: {
        videos: Array   //Type check da propriedade
    },
    methods: {
        onVideoSelect(video) {
            this.$emit('videoSelect', video);
        }
    }
}
</script>


<style>

</style>
