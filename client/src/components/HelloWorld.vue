<template>
  <div class="background-image">
    <div class="container-fluid">

      <div class="text text-center">
        <p class="display-4">THE</p> <p class="brownfont">CHAIR STORE</p> <p class="display-4">PAKAWAT</p>
        <button class="btn btn-primary" v-on:click="navigateTo('/chairs')">Go to CRUD</button>
      </div>

    </div>
  </div>
</template>
 
<script>
export default {
  name: 'HelloWorld',
  methods: {
    navigateTo(route) {
      this.$router.push(route);
    },
  },
};
</script>
 
<style scoped>
.background-image {
  text-align: center;
  background-image: url('~@/pic/bg4.jpg');
  background-size: cover;
  background-repeat: no-repeat;
  height: 100vh;
}

.container-fluid {
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
  margin-top: auto;
  /* background-color: black; */
  height: 100%;
}
.display-4{
  font-size:50px;
  font-weight: bold;
  border-color: #D2A599;
  border-width: 5px;
  color: #752d18;
}
.brownfont{
  color: #F0F4BF;
  font-weight: bold;
}
.text {
  font-size: 50px;
}
.btn-primary{
  background-color: #D2A599;
  border-color:whitesmoke ;
}
</style>
 