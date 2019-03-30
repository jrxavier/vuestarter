<template>
    <div>
        <SearchBar @termChange="onTermChange"></SearchBar>
        <!-- 
        v-bind pode ser substituido por :
        Primeiro videos é a referência para a propriedade que será usada no componente VideoList
        Segundo video é o dado que é passado para o componente  -->
        <VideoList :videos="videos"></VideoList>
    </div>
</template>


<script>
import SearchBar from './components/SearchBar';
import VideoList from './components/VideoList';


import axios from 'axios';

const KEY_API = 'AIzaSyAAtd3ZkmShI1-GE4ud-JxznFWqSO0LznA'

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
