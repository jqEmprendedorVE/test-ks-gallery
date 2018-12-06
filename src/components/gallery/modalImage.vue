<template>
    <!-- Modal -->
    <div class="modal fade" id="myPhoto" tabindex="-1" role="dialog" aria-labelledby="myModalLabel">
        <div class="modal-dialog" role="document">
            <div class="modal-content">
                <div class="modal-body">
                    <img 
                        :src="photoSelected.url" 
                        class="img-thumbnail"/>
                    <p>{{photoSelected.title}}</p>
                </div>
            </div>
        </div>
    </div>
</template>
<script>
export default {
    name: 'modalImage',
    props: {
        photoSelected: {
            url: '',
            title: ''
        }
    }
}
</script>

