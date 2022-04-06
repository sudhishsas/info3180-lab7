<script>
export default {
    data() {
        return {
          csrf_token: '',
          description: '',
          photo: ''
        }
    },
    created() {
        this.getCsrfToken();
    },
  methods: {
    uploadPhoto(){

      let uploadForm = document.getElementById('uploadForm');
      let form_data = new FormData(uploadForm);
        fetch("/api/upload", {
            method: 'POST', 
            body: form_data,
            headers: {'X-CSRFToken': this.csrf_token}
          })
          .then(function (response) {
                return response.json();
          })
          .then(function (data) {
          // display a success message
            console.log(data);
          })
          .catch(function (error) {
              console.log(error);
          });
    },
    getCsrfToken(){
      let self = this;
      fetch('/api/csrf-token')
        .then((response) => response.json())
        .then((data) => {
          console.log(data);
          self.csrf_token = data.csrf_token;
        })
    }
  }  
}
</script>

<template>
    <form  class="d-flex flex-column justify-content-center" id="uploadForm">
    <div class="input-group mx-sm-3 mb-2">
        <label>Description</label>
        <textarea name="description" v-model="description"
        id="description" class="form-control mb-2 mr-sm-2" placeholder="add a description"></textarea>
        <br>
      
        <input type="file" id="photo" name="photo" @change="selectImage">
        <button @click="uploadPhoto" class="btn btn-primary mb-2">Upload</button>
    </div>
    
 </form>


</template>

<style>
/* Add any component specific styles here */
</style>