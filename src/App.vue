<template>
  <div class="conatiner ">
    <div class="row ">
      <!-- sidebaar component -->
      <div class="col-2 ">
        <sidebaar />
      </div>
      <!-- home component -->
      <div class="col-10 " style="background-color: 	#E6E6FA;">
        <Home />

        <div class="row justify-content-evenly">
          <!-- if view is true employeeinfo component is rendered in left pane -->
          <div v-if="view" class="col-5 bg-white border border-3 rounded-5 mt-5 " style="height: 500px;">
            <EmployeeInfo />
          </div>
          <!-- if view is false employeeinfo2 component is rendered in left pane -->
          <div v-if="!view" class="col-5 bg-white border border-3 rounded-5 mt-5  " style="height: 500px;">
            <EmployeeInfo2 :emp="emp" />
          </div>
          <!-- employee view component right pane -->
          <div class="col-5 bg-white border border-3 rounded-5 mt-5 overflow-hidden" style="height: 500px;">
            <EmployeeView :getview="getview" :getemployeeinfo="getemployeeinfo" />
          </div>

        </div>

      </div>


    </div>




  </div>
</template>

<script>

import Home from './components/Home.vue'
import EmployeeInfo from './components/EmployeeInfo.vue'
import EmployeeInfo2 from './components/EmployeeInfo2.vue'
import EmployeeView from './components/EmployeeView.vue'
import sidebaar from './components/Sidebaar.vue'

export default {
  name: 'App',
  data() {
    return {
      view: true,
      emp: {}
    }
  },
  components: {
    Home,
    EmployeeInfo,
    EmployeeView,
    sidebaar,
    EmployeeInfo2
  },
  methods: {
    getview() {

      return this.view = !this.view
      console.log("view")

    },
    getemployeeinfo(emp) {

      this.emp = emp



    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  padding-left: 50px;
  padding-right: 50px;
}
</style>


