<template>
<div class="container mt-5">
    <div class="row">
      <div class="col-6">
        <div class="row">
          <!-- . Register -->
          <div class="col-12">
            <h3 class="bg-primary text-center text-light m-0 p-2 rounded-top">Form</h3>
              <form class="form-control rounded-0 rounded-bottom">
                    <!--? user form section -->


                    <appfullName v-model="userData.fullName"></appfullName>
           
                    <!-- / A form input for email. -->
                    <div class="mb-3">
                      <label for="email" class="form-label">E-mail
                      </label>
                      <input type="text" class="form-control" id="email" v-model="userData.email">
                    </div>
                    
                    <div class="mb-3">
                    
                      <!-- / A form input for password. -->
                      <label for="password" class="form-label">Password
                      </label>
                      <input type="password" class="form-control" id="password" v-model="userData.password">
                    </div>
                    
                    <!-- / A button that is used to submit the form. -->
                    
                    <div class=" d-grid gap-2">
                      <button class="btn btn-primary" @click.prevent="submitted">Sign Up</button>
                    </div>
                    
                    <!--? user.gender section -->
                    <div class="form-check">
                      <input class="form-check-input" type="radio" name="gender" id="male" value="Male" v-model="userData.gender">
                      <label class="form-check-label" for="male">
                        Male
                      </label>
                    </div>
                    <div class="form-check">
                      <input class="form-check-input" type="radio" name="gender" id="female" value="Female" v-model="userData.gender">
                      <label class="form-check-label" for="female">
                        Female
                      </label>
                    </div>
                    <div class="form-check">
                      <input class="form-check-input" type="radio" name="gender" id="iDontTell" value="I don't tell"
                        v-model="userData.gender">
                      <label class="form-check-label" for="iDontTell">
                        I don't Tell
                      </label>
                    </div>
              </form>
          </div>
        </div>
      </div>

      <!-- / USER INFORMATION OUTPUT -->
      <div class="col-6 border rounded p-0" v-if="userData.isSubmited">
        <div class="row">
          <div class="col-12">
            <h3 class="bg-warning p-2 rounded-top text-center text-light" >Member Information</h3>
            <div class="p-2">
              <p class="border-bottom mb-4 pb-2">Firstname: <span class="ms-2">{{userData.fullName}}</span></p>
              <!-- <p class="border-bottom mb-4 pb-2">Lastname:<span class="ms-2">{{userData.lastName}}</span></p> -->
              <p class="border-bottom mb-4 pb-2">E-mail:<span class="ms-2">{{userData.email}}</span></p>
              <p class="border-bottom mb-4 pb-2">Password:<span class="ms-2">{{userData.password}}</span></p>
              <p class="border-bottom mb-4 pb-2">Gender:<span class="ms-2">{{userData.gender}}</span></p>
              <p class="border-bottom mb-4 pb-2">Is you suitable:<span class="ms-2">{{userData.suitable}}</span></p>
            </div>
          </div>
        </div>
      </div>
    </div>
</div>
</template>

<script>

import fullName from './components/full-name.vue'

export default {
 components:{
  "appfullName":fullName
 },
  
  name: 'App',
  data(){
    return{
      userData:{
        // firstName:'',
        // lastName:'',
        fullName:'Laz Ziya',
        email:'',
        password:null,
        gender:'',
        suitable:'',
        isSubmited:false
      }
    }
  },
  methods:{
    // Checking if the user has filled in the form.
    submitted(){
      this.userData.isSubmited=true
      if (this.userData.fullName && this.userData.email && this.userData.password && this.userData.gender){
        this.userData.suitable = 'You are okey'
      }else{
        this.userData.suitable = 'Please fill in the information'

      }
    }
  }
}
</script>

<style>
#app {

}
</style>
