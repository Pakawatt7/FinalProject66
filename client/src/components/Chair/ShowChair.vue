<template>
    <div class="bg-Show">
        <h1>Detail chair</h1>
        <hr>
        
          <p></p>
        <p>ID :{{ chair.id }}</p>
        <p>Name :{{ chair.ChairName }}</p>
        <p>Material :{{ chair.ChairMaterial }}</p>
        <p>Color :{{ chair.ChairColor }}</p>
        <p>Size :{{ chair.ChairSize }} cm</p>
        <p>Price :{{ chair.ChairPrice }} baht</p>
        <p>
            <button v-on:click="navigateTo('/chair/edit/'+chair.id)">Edit chair</button>
            <button v-on:click="navigateTo('/chairs')">ย้อนกลับ</button>
        </p>
        <hr>
    </div>
</template>

<script>

import ChairService from '@/services/ChairService'

export default {

    data() {
        return {
            chair: ""
        }
    },

    methods: {
        navigateTo(route) {
            // ตรง$router ต้องตั้งให้ตรง folder ของ route
            this.$router.push(route)
        }
    },

    async created() {
        try {
            let chairId = this.$route.params.chairId
            this.chair = (await ChairService.show(chairId)).data
        } catch (error) {
            console.log(error)
        }
    }

}

</script>

<style scoped>
.bg-Show{
    background-color: #fbe9df;
    height: 100vh;
    padding: 100px;
}
h1{
    color: #b58274;
    margin-bottom: 10px;
    font-size: 50px;
    text-decoration: underline ;
    padding: 5px;
}
</style>