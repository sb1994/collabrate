<template>
  <div>
    <loggedout-navbar></loggedout-navbar>
    <div class="container">
      <p>Register vue</p>
        <div class="form-group">
          <label for="name" class="label-control">Name</label>
          <input type="text" id="name" name="name" value="" class="form-control" v-model="form.name">
        </div>
        <div class="form-group">
          <label for="email" class="label-control">Email</label>
          <input type="text" id="email" name="email" value="" class="form-control" v-model="form.email">
        </div>
        <div class="form-group">
          <label for="password" class="label-control">Password</label>
          <input type="password" name="password" id="password" value="" class="form-control" v-model="form.password">
        </div>
        <button type="button" name="button"  v-on:click="registerUser">Register</button>
    </div>
  </div>
</template>
<script>
import {registerUrl} from '../../config'
import LoggedoutNavBar from '../../components/LoggedoutNavbar.vue';
export default{
  components:{
    'loggedout-navbar':LoggedoutNavBar
  },
  data(){
    return{
      form:{
        name:"",
        email:"",
        password:"",

      },
      error:{},
      isProssessing:false
    }
  },
  methods:{
    registerUser(){
      console.log(registerUrl);
      axios.post(registerUrl,this.form)
          .then(response=>{
            if (response.status===200) {
              this.$router.push('/login');
            }
          })
    }
  },
}

</script>
<style>
</style>
