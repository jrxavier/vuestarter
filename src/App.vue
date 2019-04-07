<template>
    <div class="container">
        <SearchBar @termChange="onTermChange"></SearchBar>
        <VideoDetail :video="selectVideo"></VideoDetail>
        <!-- 
        v-bind pode ser substituido por :
        Primeiro videos é a referência para a propriedade que será usada no componente VideoList
        Segundo video é o dado que é passado para o componente  -->
        <VideoList @videoSelect="onVideoSelect" :videos="videos"></VideoList>
    </div>
</template>

<script>
import SearchBar from './components/SearchBar';
import VideoList from './components/VideoList';
import VideoDetail from './components/VideoDetail';

import axios from 'axios';

const KEY_API = 'AIzaSyAAtd3ZkmShI1-GE4ud-JxznFWqSO0LznA'

export default {
    name: 'App',
    components: {
           //CUIDADO: Muitas vezes isso é esquecido.
        SearchBar ,
        VideoList,
        VideoDetail
    },
    data() {
        return {
            videos: [],
            selectVideo: null
        }
    },
    methods: {
        //Bind do método ao evento é feito lá no template
        onTermChange(searchTerm) {
            //searchTerm poderia ser qq nome e se refere ao event.target.value
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
        },
        onVideoSelect(video) {
            this.selectVideo = video;
        }
    }
}
</script>
