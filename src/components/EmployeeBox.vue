<template>
    <div class="conatiner">
        <div class="row d-flex justify-content-around">
            <div class="col-1"></div>
            <!-- profile pic -->
            <div class="col-2"><i class="bi bi-person-circle fas  fa-3x "></i></div>
            <!-- name -->
            <div class="col-5"> {{ employee.displayname }}</div>
            <!-- view button -->
            <div class="col-4"> <button type="button" v-on:click="view()" class="btn btn-lg  ">View</button>
            </div>
        </div>
    </div>
</template>
<script>
import axios from 'axios'
export default {
    name: "EmployeeBox",
    props: {
        employee: Object,
        getview: Function,
        getemployeeinfo: Function

    },
    data() {
        return {
            id: null,
            emp: null,
            name: 'utkarsh'

        }
    },


    methods: {
// method triggred by view button
        async view() {
            // to get view status from app.vue
            this.getview();
            await axios
                .get(`https://backend-data-kbmy.onrender.com/Employee/${this.id}`)
                .then((res) => (this.emp = res.data))
                .catch((err) => console.log(err));


            this.getemployeeinfo(this.emp)

        }
    },
    mounted() {
        this.id = this.employee.id
    }

};
</script>
<style>
.btn {
    background-color: #8B008B;
    
    color: white;
}


</style>