

<template>
    <div class="w-96 ">
        <h4 class="text-3xl text-gray-700 mb-5">Debugging Form</h4>
        <div class="p-10 rounded-md shadow-md bg-white" style="width: 550px;margin: 0;align-items: center;">
            <div class="w-full text-ceenter px-4 py-3 ">
                <label class="block mb-3 text-gray-600" for="">Error Code</label>
                <input v-model="name" id="name" type="text"
                    class="border border-gray-500 rounded-md inline-block  py-2 px-3 w-full text-gray-600 tracking-wider" />
            </div>
            <div class="w-full text-ceenter px-4 py-3 ">
                <label class="block mb-3 text-gray-600" for="">Error Description</label>
                <input v-model="description" id="description" type="text"
                    class="border border-gray-500 rounded-md inline-block py-2 px-3 w-full text-gray-600 tracking-widest" />
            </div>

            <div>
                <button @click="finishPayment"
                    class="w-full text-ceenter px-4 py-3 bg-green-500 rounded-md shadow-md text-white font-semibold">
                    Kaydet
                </button>
            </div>
        </div>
    </div>
</template>

  
  
<script>
import axios from "axios";

export default {
    name: "Form",
    data() {
        return {
            name: "",
            email: ""
        };
    },
    methods: {
        async submitForm() {
            try {
                const response = await axios.post("/api/form", {
                    name: this.name,
                    email: this.email
                });
                console.log(response.data);
            } catch (error) {
                console.error(error);
            }
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