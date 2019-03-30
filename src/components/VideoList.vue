<template>
    <ul>
        Video List
        {{videos.length}}
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
