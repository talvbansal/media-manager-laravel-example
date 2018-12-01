<template>
	<div>
		<media-modal v-if="showMediaManager" @media-modal-close="showMediaManager = false">
			<media-manager
					:is-modal="true"
					selected-event-name="editor"
					@media-modal-close="showMediaManager = false"
			>
			</media-manager>
		</media-modal>

		<div class="form-group">
			<div class="input-group">
				<input type="text" class="form-control" name="page_image" id="page_image" alt="Image thumbnail" placeholder="Page Image" v-model="pageImage">
				<span class="input-group-btn">
                <button type="button" class="btn btn-default" @click="showMediaManager = true">Select Image</button>
            </span>
			</div>

			<div>
				<img v-if="pageImage" class="img img-responsive" id="page-image-preview" style="margin-top: 3px; max-height:250px;" :src="pageImage"/>
				<span v-else class="text-muted small">No Image Selected</span>
			</div>
		</div>


	</div>

</template>

<script>
    export default {

        data() {
            return {
                showMediaManager: false,
                pageImage: null,
            }
        },

        mounted() {
            window.eventHub.$on('media-manager-selected-editor', (file) => {
                // Do something with the file info...
                console.log(file.name);
                console.log(file.mimeType);
                console.log(file.relativePath);
                console.log(file.webPath);
                this.pageImage = file.webPath;

                // Hide the Media Manager...
                this.showMediaManager = false;
            });
        }
    }
</script>
