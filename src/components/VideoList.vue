<template>
    <ul>
        <VideoListItem 
            v-for="videoItem in videos"
            v-bind:video="videoItem"
            >
        </VideoListItem>    
    </ul>
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
