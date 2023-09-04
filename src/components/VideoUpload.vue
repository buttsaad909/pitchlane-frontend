<template>
    <div>
        <h2>Upload Video</h2>
        <div class="custom-file">
            <input type="file" @change="handleFileChange" accept="video/*">
            <button type="button" class="btn btn-primary" @click="uploadVideo">Upload</button>
        </div>
    </div>
</template>

<script>
import axios from 'axios';

export default {
    data() {
    return {
        selectedFile: null,
    };
  },
  methods: {
    handleFileChange(event) {
      this.selectedFile = event.target.files[0];
      console.log(this.selectedFile)
    },
    uploadVideo() {
      if (this.selectedFile) {
        const formData = new FormData();
        formData.append('video', this.selectedFile);
        axios.post('https://clumsy-pig-hospital-gown.cyclic.app/api/upload', formData, {
          headers: {
            'Content-Type': 'multipart/form-data',
          },
        })
        .then(res => { 
          console.log(res)
        })
        .catch(error => {
          console.log(error)
        });
      }
    },
  },
}
</script>

<style>

</style>