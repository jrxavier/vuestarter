<template>
    <div>
        <input type="text" @input="onInput">
    </div>
</template>

<script>
export default {
    name: 'SearchBar',
    methods: {
        onInput: function(event) {
            this.$emit('termChange', event.target.value);
        }
    }
}
</script>

<!-- a definição SCOPE garante que o CSS só se aplica ao componente em questão -->
<style scoped>
    input {
        width: 75%;
    }

    div {
        text-align: center;
        margin: 20px;
    }
</style>
