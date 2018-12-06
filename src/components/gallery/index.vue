<template>
    <div>
        <h3>Listado de fotos</h3>
        <div class="col-md-10 col-md-offset-1">
            <div
                class="col-xs-2 col-sm-2 col-md-2" 
                v-for="photo in photos" :key="photo.id">
                <img 
                    :src="photo.thumbnailUrl" 
                    :alt="photo.thumbnailUrl" 
                    class="img-thumbnail"
                    @click="showImage(photo.id)">
            </div>
        </div>

        <modalImage :photoSelected="this.photoSelected" />        
    </div>
</template>
<script>
import axios from 'axios';
import modalImage from './modalImage.vue';

export default {
    name: 'GalleryPhotos',
    components: {
        modalImage
    },
    data() {
      return {
        photos: {},
        photoSelected: {
            url: '',
            title: ''
        }
      }
    },
    async created() {
        this.photos = await axios.get('https://jsonplaceholder.typicode.com/photos?albumId=1')
        .then(res => res.data)
    },
    methods: {
        showImage(id) {
            const photo = this.photos[id]
            this.photoSelected = {
              url: photo.url,
              title: photo.title  
            }

            $('#myPhoto').modal('show')
        }
    }
}
</script>
<style>
.img-thumbnail {
    cursor: pointer;
}
</style>
