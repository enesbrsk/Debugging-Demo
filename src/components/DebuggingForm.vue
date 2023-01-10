

<template>
    <form id="debuggingForm">
        <div class="w-96 ">
            <h4 class="text-3xl text-gray-700 mb-5">Hata Ekleme Formu</h4>
            <div class="p-10 rounded-md shadow-md bg-white" style="width: 550px;margin: 0;align-items: center;">
                <div class="w-full text-ceenter px-4 py-3 ">
                    <label class="block mb-3 text-gray-600" for="">Hata Kodu</label>
                    <input v-model="name" id="debugName" type="text"
                        class="border border-gray-500 rounded-md inline-block  py-2 px-3 w-full text-gray-600 tracking-wider" />
                </div>
                <div class="w-full text-ceenter px-4 py-3 ">
                    <label class="block mb-3 text-gray-600" for="">Hata Açıklaması</label>
                    <input v-model="description" id="debugDescription" type="text"
                        class="border border-gray-500 rounded-md inline-block py-2 px-3 w-full text-gray-600 tracking-widest" />
                </div>

                <div>
                    <button v-on:click.prevent="post"
                        class="w-full text-ceenter px-4 py-3 bg-green-500 rounded-md shadow-md text-white font-semibold">
                        Kaydet
                    </button>
                </div>
            </div>
        </div>
    </form>
</template>

  
  
<script>
import axios from "axios";


export default {
    name: 'DebuggingForm',
    components: {
        Headers
    },
    methods: {
        post: function () {
            let formData = new FormData(document.getElementById("debuggingForm"));

            // Simple POST request with a JSON body using fetch
            const requestOptions = {
                headers: { 'Content-Type': 'application/json' },
                method: "POST",
                body: JSON.stringify({
                    debugName: document.getElementById("debugName").value,
                    debugDescription: document.getElementById("debugDescription").value
                })
            };
            fetch("https://localhost:7160/SaveDebugging", requestOptions)
                .then(response => response.json())
                .then(data => {
                    (console.log(data))
                    location.reload();
                });

        }
    }
};
</script>
<style>
#debugging-form {
    background-color: black;
    box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2);
    transition: 10.3s;
    border-radius: 5px
}
</style>