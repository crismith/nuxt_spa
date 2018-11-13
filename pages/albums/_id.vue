<template lang="html">
    <div class="container">
        <header class="has-text-centered">
            <h1 class="title has-text-centered">{{album.title}}</h1>
            <nuxt-link to="/">Regresar </nuxt-link>
            <br>
            <br>
        </header>
        <div class="columns is-multiline">
            <div class="column is-one-quarter" v-for="photo in photos" :key="photo.id">
                <img :src="photo.url" alt="photo.title">
            </div>
        </div>
    </div>
</template>

<script>
    import route from 'vue-router';
    import axios from 'axios';
    import env from '../../config/env';
    export default{
        name: 'albumId',
        data(){
            return {
                album : {},
                photos: []
            }
        },
        created: async function (){
            let albumRes = await axios.get(`${env.endpoint}/albums/${this.$route.params.id}`)
            this.album = albumRes.data
            let photosRes = await axios.get(`${env.endpoint}/albums/${this.$route.params.id}/photos`)
            this.photos = photosRes.data
            // axios.get(`${env.endpoint}/albums/${this.$route.params.id}`)
            // .then( res => {
            // })
            // .catch( err => {
            //     console.log('err::',err)
            // })

            // axios.get(`${env.endpoint}/albums/${this.$route.params.id}/photos`)
            // .then( res => {
            //     this.photos = res.data
            // })
            // .catch( err => {
            //     console.log('err::',err)
            // })
            // console.log('ruta',this.$route.params.id)
        }
    }
</script>
<style lang='css'>
    
</style>