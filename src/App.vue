<template>
    <div>
        <SearchBar @termChange="onTermChange"></SearchBar>
    </div>
</template>


<script>
import SearchBar from './components/SearchBar';

export default {
    name: 'App',
    components: {
        SearchBar    //CUIDADO: Muitas vezes isso é esquecido.
    },
    methods: {
        onTermChange(searchTerm) {
            //searchTermo poderia ser qq nome e se refere ao event.target.value
            console.log(searchTerm);
        }
    }
}
</script>
