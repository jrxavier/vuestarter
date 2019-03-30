<template>
    <ul>
        <VideoListItem 
            v-for="videoItem in videos"
            :video="videoItem"
            :key="videoItem.etag"   
            >
        </VideoListItem>    
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
    }
}
</script>


<style>

</style>
