<script>
import UploadForm from '@/components/UploadForm.vue'
export default {
  
    data() {
        return {
            description: "description",
            photo: undefined,
            message: "Hello World! This is Lab 7 {show upload form  }"
        };
    },
    components: { UploadForm }
}
</script>

<template>
    <div class="container">
      <div class="text-center">
        <img alt="Vue logo" class="logo" src="@/assets/logo.svg" width="125" height="125" />
        <h1>{{ message }}</h1>
        <UploadForm/>
      </div>
    </div>
</template>

<style>
/* Add any component specific styles here */
</style>