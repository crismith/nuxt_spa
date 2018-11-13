<template lang="html">
    <div class="column is-one-quarter">
        <div class="box">
            <h4>{{album.title}}</h4>
            <nuxt-link :to="`/albums/${album.id}`" class="button is-primary">Ver album</nuxt-link>
        </div>
    </div>
</template>

<script>
    export default{
        name: 'AlbumCard',
        props: {
            album: Object
        },
        data(){
            return {

            }
        }
    }
</script>
<style lang='css'>
    .box{
        padding: 1em;
    }
    h4{
        min-height: 4.5em;
    }
</style>