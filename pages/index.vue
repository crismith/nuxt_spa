<template lang="html">
    <div class="container">
        <h1 class="title">Mis albunes</h1>
        <div class="columns is-multiline">
            <AlbumCard :album="album" v-for="album in albums" :key="album.id" />
        </div>
    </div>
</template>
<script>
    import axios from 'axios';
    import env from '../config/env';
    import AlbumCard from '../components/AlbumCard';
    export default{
        name: 'IndexPage',
        data(){
            return {
                albums : []
            }
        },
        components:{
            AlbumCard
        },
        created: async function (){
            let albumsRes = await axios.get(`${env.endpoint}/albums`)
            this.albums = albumsRes.data

            // axios.get(`${env.endpoint}/albums`)
            // .then( res => {
            // })
            // .catch( err => {
            //     console.log('err::',err)
            // })
        }
    }
</script>
<style scoped>
    
</style>