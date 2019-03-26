<template>
    <div>
        <SearchBar @termChange="onTermChange"></SearchBar>
    </div>
</template>


<script>
import SearchBar from './components/SearchBar';
import axios from 'axios';

const KEY_API = ''

export default {
    name: 'App',
    components: {
        SearchBar    //CUIDADO: Muitas vezes isso é esquecido.
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
            }).then(response => console.log(response))
        }
    }
}
</script>
