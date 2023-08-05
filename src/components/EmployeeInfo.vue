<template>
  <div class="container">
    <div class="row  d-flex justify-content-around mt-3">
      <div class="col fw-bold fs-5"> Employee Info</div>
    </div>
    <div class="row">
      <br>
      <br>
    </div>
    <div class="row justify-content-start">


      <div class="col-12">
        <form>
           <!-- display name input  -->
          <div class="row mb-3">
            <div class="col-sm-12 ">
              <input type="text" class="form-control form-control-lg" v-model="displayname" id="colFormLabelLg"
                placeholder="Display Name">
            </div>
          </div>
           <!-- login id input  -->
          <div class="row mb-3">          
            <div class="col-sm-12 ">
              <input type="email" class="form-control form-control-lg" v-model="loginid" id="colFormLabelLg"
                placeholder="LoginId">
            </div>
          </div>
           <!-- password input  -->
          <div class="row mb-3">            
            <div class="col-sm-12 ">
              <input type="password" class="form-control form-control-lg" v-model="passowrd" id="colFormLabelLg"
                placeholder="Password">
            </div>
          </div>
         

        </form>


      </div>
      <!-- status toggle -->
      <div class="form-check form-switch d-flex mb-3 mt-3 ">


        <div class='col-1 fw-bold fs-6'>status</div>
        <div class="col-10"></div>
        

        <div class='col-1'> <input class="form-check-input " type="checkbox" v-model="status" role="switch"
            id="flexSwitchCheckChecked" checked /></div>

      </div>
        <!-- save  button -->
      <div class="row mt-4 ">
        <div class="col-12">
          <button type="button" class="btn-lg btn " v-on:click="addempl"> save </button>
        </div>
      </div>

      

    </div>
  </div>
</template>
<script>
import axios from 'axios'
import swal from 'sweetalert'
export default {
  name: 'EmployeeInfo',
  data() {
    return {
      displayname: '',
      loginid: '',
      password: '',
      status: '',

    }
  },
  methods: {
    // add employee function triggred by save button
    addempl() {
      console.log(this.displayname, this.loginid, this.password)
      const newempl = {
        displayname: this.displayname,
        loginid: this.loginid,
        password: this.password,
        status: this.status

      }
// axios to post data on api
      axios({
        method: 'post',
        url: 'https://backend-data-kbmy.onrender.com/Employee',
        data: JSON.stringify(newempl),
        headers: {
          "Content-Type": "application/json"
        }




      }).then(() => {
        swal({
          text: "employee added successfully",
          icon: "success",
        })

      })
        .catch((err) => {
          console.log(err)
        })
    }
  }
}



</script>
<style>
.btn {
   width: 100%;
   min-width: 50px;  
   max-width: 160px; 
}



</style>