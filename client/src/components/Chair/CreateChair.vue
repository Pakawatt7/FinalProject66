<template>
    <div class="Box-Create">
        <h1>CREATE CHAIR</h1>
        <form v-on:submit.prevent="createChair">
            <p>Name : <input type="text" v-model="chair.ChairName"></p>
            <p>Material : <input type="text" v-model="chair.ChairMaterial"> </p>
            <p>Color : <input type="text" v-model="chair.ChairColor"> </p>
            <p>Size: <input type="text" v-model="chair.ChairSize"> cm.</p>
            <p>Price : <input type="text" v-model="chair.ChairPrice"> baht</p>
            <p><button type="submit">Create chair</button></p>
        </form>
         <button v-on:click="navigateTo('/chairs')">ย้อนกลับ</button>
        
        <hr>
    </div>
</template>
<script>

import ChairService from '@/services/ChairService'
export default {
    data() {
        return {
            chair: {
                ChairName: '',
                ChairMaterial: '',
                ChairColor: '',
                ChairSize: '',
                ChairPrice: '',
            }
        }
    },
    methods: {
        navigateTo(route) {
            this.$router.push(route).catch(err => {})
        },
        async createChair() {
            try {
                await ChairService.post(this.chair)
                this.$router.push('/chairs')
            } catch (err) {
                console.log(err)
            }
        }
    }
};
</script>
<style scoped>
.Box-Create{
    background-color: #fbe9df;
    height: 100%;
    padding: 100vh;
}
h1{
    color: #b58274;
    margin-bottom: 10px;
    font-size: 50px;
    text-decoration: underline ;
    padding: 5px;
}
    </style>