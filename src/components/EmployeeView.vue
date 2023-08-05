<template>
  <div class="conatiner">
    <div class="row d-flex justify-content-around mb-3 mt-4">
      <div class=" col fw-bold fs-5 ">
        View Employees ({{ employees.length }})
      </div>

      <div class="col">
        <form class="d-flex" role="search">
          <input class="form-control me-2" type="search" placeholder="Search" v-model="search" aria-label="Search">

        </form>

      </div>

    </div>

    <div class="row mt-5 ">
      <div v-for="employee of employeelist" :key="employee.id" class="col-12 d-flex flex-column mb-3 fw-bold fs-5">
        <EmployeeBox :employee="employee" :getview="getview" :getemployeeinfo="getemployeeinfo"> </EmployeeBox>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
import EmployeeBox from "./EmployeeBox.vue";
export default {
  name: "Employeeview",
  components: { EmployeeBox },



  props: {
    getview: Function,
    getemployeeinfo: Function

  },


  data() {
    return {
      baseURL: "https://backend-data-kbmy.onrender.com",
      employees: [],
      search: ''
    };
  },
  methods: {
    async getemployee() {
      await axios
        .get(`${this.baseURL}/Employee`)
        .then((res) => (this.employees = res.data))
        .catch((err) => console.log(err));
    },
  },
  computed: {
    employeelist() {
      if (this.search.trim().length > 0) {
        return this.employees.filter((res) => res.displayname.includes(this.search.trim()))

      }
      return this.employees
    }

  },
  mounted() {
    this.getemployee();
  },
};
</script>