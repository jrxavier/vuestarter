<template>
    <div>
        <SearchBar @termChange="onTermChange"></SearchBar>
        <VideoList></VideoList>
        {{ videos.length }}
    </div>
</template>


<script>
import SearchBar from './components/SearchBar';
import VideoList from './components/VideoList';


import axios from 'axios';

const KEY_API = ''

export default {
    name: 'App',
    components: {
           //CUIDADO: Muitas vezes isso é esquecido.
        SearchBar ,
        VideoList
    },
    data() {
        return {
            videos: []
        }
    },
    methods: {
        onTermChange(searchTerm) {
            //searchTermo poderia ser qq nome e se refere ao event.target.value
            console.log(searchTerm);
            
            axios.get('https://www.googleapis.com/youtube/v3/search', {
                params: {
                    key: KEY_API,
                    type: 'video',
                    part: 'snippet',
                    q: searchTerm
                }
            }).then(response => {
                this.videos = response.data.items
            })
        }
    }
}
</script>
