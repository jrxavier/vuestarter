<template>
    <li class="list-group-item media" @click="onVideoSelect">
        <img class="mr-3"  :src="thumbnailUrl" />
        <div class="media-body">
            {{ video.snippet.title }}
        </div>
        
    </li>
</template>

<script>
export default {
    name: 'VideoListItem',
    props: ['video'],
    computed: {
        thumbnailUrl() {
            return this.video.snippet.thumbnails.default.url;
        }
    },
    methods: {
        onVideoSelect() {
            this.$emit('videoSelect', this.video);
        }
    }
}
</script>

<!-- Scoped : só se aplica ao componente
css: trabalha a imagem e o texto na mesma linha. com cursos na forma de ponteiro e cor cinza na hora que
passa o mouse por cima da área da imagem -->
<style scoped> 
    li {
        display: flex;
        cursor: pointer;
    }

    li:hover {
        background-color: #eee;
    }

</style>
