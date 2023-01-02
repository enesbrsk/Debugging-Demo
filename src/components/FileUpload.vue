<template >
  <div class="form">
    <form>
      <div class="flex items-center justify-center w-full">
        <label for="dropzone-file"
          class="flex flex-col items-center justify-center w-full h-64 border-2 border-gray-300 border-dashed rounded-lg cursor-pointer bg-gray-50 dark:hover:bg-bray-800 dark:bg-gray-700 hover:bg-gray-100 dark:border-gray-600 dark:hover:border-gray-500 dark:hover:bg-gray-600">
          <div class="flex flex-col items-center justify-center pt-5 pb-6">


            <svg v-if="fileStatus == false" aria-hidden="true" class="w-10 h-10 mb-3 text-gray-400" fill="none"
              stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
                d="M7 16a4 4 0 01-.88-7.903A5 5 0 1115.9 6L16 6a5 5 0 011 9.9M15 13l-3-3m0 0l-3 3m3-3v12"></path>
            </svg>
            <p v-if="fileStatus == false" class="mb-2 text-sm text-gray-500 dark:text-gray-400"><span
                class="font-semibold">Yüklemek için
                tiklayin</span> ya da dosyayi sürükleyin</p>

            <svg v-if="fileStatus == true" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24"
              stroke-width="1.5" stroke="currentColor" class="w-10 h-10 mb-3 text-gray-400">
              <path stroke-linecap="round" stroke-linejoin="round"
                d="M19.5 14.25v-2.625a3.375 3.375 0 00-3.375-3.375h-1.5A1.125 1.125 0 0113.5 7.125v-1.5a3.375 3.375 0 00-3.375-3.375H8.25m2.25 0H5.625c-.621 0-1.125.504-1.125 1.125v17.25c0 .621.504 1.125 1.125 1.125h12.75c.621 0 1.125-.504 1.125-1.125V11.25a9 9 0 00-9-9z" />
            </svg>
            <p v-if="fileStatus == true" class="mb-2 text-sm text-gray-500 dark:text-gray-400"><span
                class="font-semibold">Başarılı bir şekilde yüklendi</span></p>

          </div>
          <input id="dropzone-file" ref="fileInput" @change="uploadFile" type="file" class="hidden" />

          <button type="submit">Yükle</button>
        </label>
      </div>
    </form>
  </div>

</template>

<script>
import axios from 'axios';

export default {
  data() {
    return {
      fileStatus: false,
    };
  },
  methods: {

    async uploadFile() {
      this.fileStatus = true
      const file = this.$refs.fileInput.files[0];
      const formData = new FormData();
      formData.append('file', file);

      try {
        fileStatus: false
        //const response = await axios.post('/server/upload', formData);

        console.log(file.name)
        //console.log(response.data);
      } catch (error) {
        console.error(error);
      }
    }
  }
}
</script>

<style>
.form {

  margin: auto !important;
  width: 500px !important;
  height: max-content !important;
}

.file {
  margin: auto;
  width: 50%;
  align-items: center;
  border: 3px solid green;
  padding: 10px;
  background-color: aliceblue;
}

.file-card {
  box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2);
  transition: 0.3s;
  width: 350px;
  height: 350px;
  background-color: red;
}
</style>