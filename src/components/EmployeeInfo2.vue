<template>
  <div class="container">
    <div class="row  d-flex justify-content-around mt-3">
      <div class="col fw-bold fs-5"> Employee Info</div>
      <!-- edit button -->
      <div class="col fw-bold fs-5">
        <button type="button" v-on:click="editemployee" class="btn-light shadow-none  ">Edit</button>
      </div>


    </div>
    <div class="row">
      <br>
      <br>
    </div>
    <div class="row justify-content-start">


      <div class="col-12">
        <form>
          <!-- display name input -->
          <div class="row mb-3">
            <div class="col-sm-12 ">
              <input type="text" class="form-control form-control-lg" v-model="emp.displayname" id="colFormLabelLg"
                placeholder="Display Name">
            </div>
          </div>
          <!-- login id input -->
          <div class="row mb-3">          
            <div class="col-sm-12 ">
              <input type="email" class="form-control form-control-lg" v-model="emp.loginid" id="colFormLabelLg"
                placeholder="LoginId">
            </div>
          </div>
          <!-- password input -->
          <div class="row mb-3">           
            <div class="col-sm-12 ">
              <input type="passoword" class="form-control form-control-lg" v-model="emp.passowrd" id="colFormLabelLg"
                placeholder="Password">
            </div>
          </div>
         

        </form>


      </div>
      <!-- status toggle -->
      <div class="form-check form-switch d-flex justify-content-around mb-3 ">
        <div class='col-1 fw-bold fs-6'>status</div>
        <div class="col-10"></div>

        <div class='col-1'> <input class="form-check-input " type="checkbox" v-model="emp.status" role="switch"
            id="flexSwitchCheckChecked" checked /></div>

      </div>


    </div>
  </div>
</template>
<script>
import axios from 'axios'
import swal from 'sweetalert'
export default {

  name: 'EmployeeInfo2',
  props: {
    emp: Object
  },
  data(){
    return{
      baseURL: "https://backend-data-kbmy.onrender.com",
      displayname: '',
      loginid: '',
      password: '',
      status: '',
     
    }
  },
  methods:{
  //  method to edit employee triggred by edit button
    async editemployee(){
      
      const newempl = {
        displayname: this.emp.displayname,
        loginid: this.emp.loginid,
        password: this.emp.password,
        status: this.emp.status

      }
      
      await axios.put(`${this.baseURL}/Employee/${this.emp.id}`,
                    newempl)
                    .then(() => {
                        
                        swal({
                            text: "employee has been updated successfully",
                            icon: "success"
                        })
                    }).catch(err => console.log('err', err));

    }
  },

  
  


}

</script>
