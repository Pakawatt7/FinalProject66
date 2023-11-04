<template>
    <div class="bg-edit">
        <h1>EDIT CHAIR</h1>
        <form v-on:submit.prevent="editChair">
          <p>Name : <input type="text" v-model="chair.ChairName"></p>
          <p>Material : <input type="text" v-model="chair.ChairMaterial"> </p>
          <p>Color : <input type="text" v-model="chair.ChairColor"> </p>
          <p>Size : <input type="text" v-model="chair.ChairSize"> cm.</p>
          <p>Price : <input type="text" v-model="chair.ChairPrice"> baht</p>
          <p><button type="submit">Edit chair</button></p>
          <button v-on:click="navigateTo('/chairs')">ย้อนกลับ</button>
      </form>
        <hr>
        <h5>Display Example By Id</h5>
        <p>ID :{{ chair.id }}</p>
        <p>Name :{{ chair.ChairName }}</p>
        <p>Material :{{ chair.ChairMaterial }}</p>
        <p>Color :{{ chair.ChairColor }}</p>
        <p>Size :{{ chair.ChairSize }} cm</p>
        <p>Price :{{ chair.ChairPrice }} baht</p>
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
      this.$router.push(route)
    },

    async editChair() {
      try {
        await ChairService.put(this.chair)
        this.$router.push({ name: 'chairs' })
      } catch (err) {
        console.log(err)
      }
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
.bg-edit{
  background-color: #fbe9df;
    height: 100%;
    padding: 100px;
}
h1{
  color: #b58274;
  margin-bottom: 15px;
  font-size: 50px;
  text-decoration: underline ;
  padding: 5px;
}
h5{
  color: #b58274;
  text-decoration: underline;
  background-color: #fbe9df;
}
</style>