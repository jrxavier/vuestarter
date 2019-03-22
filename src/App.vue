<template>
    <div>
        <SearchBar></SearchBar>
    </div>
</template>


<script>
import SearchBar from './components/SearchBar';

export default {
    name: 'App',
    components: {
        SearchBar    //CUIDADO: Muitas vezes isso é esquecido.
    }
}
</script>
