<template>
    <div class="background-image">
        <div class="container-xl">
            <div class="">
                <div class="table-wrapper">
                    <div class="table-bgc">
                        <div class="table-title">
                            <div class="row">
                                <div class="col">
                                    <h2><b>CHAIR STORE</b></h2>
                                    <div class="col-btn">
                                        <a class="btn btn-secondary" v-on:click="navigateTo('chair/create')"><i
                                                class="material-icons">&#xE147;</i> <span>Add New Chair</span></a>

                                    </div>
                                </div>
                            </div>
                        </div>
                        <div class="container-fluid ">
                            <table class="table table-striped table-hover table-bordered">
                                <thead>
                                    <tr>
                                        <th>#</th>
                                        <th>Name <i class=""></i></th>
                                        <th>Material</th>
                                        <th>Color <i class=""></i></th>
                                        <th>Size(W,l,h)</th>
                                        <th>Price <i class=""></i></th>
                                        <th>Actions</th>
                                    </tr>
                                </thead>
                                <tbody>


                                    <tr v-for="chair in chairs" v-bind:key="chair.id">
                                        <td>{{ chair.id }}</td>
                                        <td>{{ chair.ChairName }}</td>
                                        <td>{{ chair.ChairMaterial }}</td>
                                        <td>{{ chair.ChairColor }}</td>
                                        <td>{{ chair.ChairSize }} cm.</td>
                                        <td>{{ chair.ChairPrice }} baht.</td>
                                        <td>
                                            <a class="view" title="View" data-toggle="tooltip"
                                                v-on:click="navigateTo('chair/' + chair.id)"><i
                                                    class="material-icons">&#xE417;</i> </a>

                                            <a class="edit" title="Edit" data-toggle="tooltip"
                                                v-on:click="navigateTo('chair/edit/' + chair.id)"><i
                                                    class="material-icons">&#xE254;</i> </a>

                                            <a class="delete" title="Delete" data-toggle="tooltip"
                                                v-on:click="deleteChair(chair)"><i class="material-icons">&#xE872;</i> </a>
                                        </td>
                                    </tr>
                                </tbody>
                            </table>
                        </div>
                    </div>

                </div>
            </div>
        </div>
    </div>
</template>

<script>

import ChairService from '@/services/ChairService'

export default {
    data() {
        return {
            chairs: ""
        }
    },
    methods: {

        navigateTo(route) {
            this.$router.push(route)
        },

        async deleteChair(chair) {
            let result = confirm("Want to delete chair?")
            if (result) {
                try {
                    await ChairService.delete(chair)
                    this.refreshData()
                } catch (err) {
                    console.log(err)
                }
            }
            console.log(chair);
        },
        async refreshData() {
            this.chairs = (await ChairService.index()).data
        }
    },

    async created() {
        this.chairs = (await ChairService.index()).data
        console.log(this.chairs);
    }

}
</script>


<style scoped>
.background-image {
    text-align: center;
    background-image: url('~@/pic/bg4.jpg');
    opacity: 0.9;
    background-size: cover;
    background-repeat: no-repeat;
    height: 100vh;
}
.container-xl {
    display: flex;
    align-items: center;
    justify-content: center;
    height: 100%;
}
.container-fluid {
    margin-top: 10px;
    display: flex;
    justify-content: center;
    align-items: center;
    text-align: center;
}
.table-bgc {
    background-color: #fbe9df;
    border-radius: 20px;
}
.view {
    color: rgb(179, 84, 16);
}
.edit{
    color: rgb(5, 113, 5);
}
.delete{
    color: rgb(210, 42, 42);
}
.material-icons {
    cursor: pointer;
}
h2 {
    margin-top: 70px;
    color: #b58274;
    font-size: 50px;
    text-decoration: underline ;
    padding: 5px;
}
.btn {
    color: rgb(255, 255, 255);
}

.btn-secondary {
    position: absolute;
    background-color:#836953;
    right: 25px;
    bottom: 10px;
}


</style>
   