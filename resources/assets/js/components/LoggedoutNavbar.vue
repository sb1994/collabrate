<template>
  <!--this navbar is shown whrn the user has been logged out
  and is returned to the login/register pages -->
  <nav class="navbar navbar-default">
    <div class="container-fluid">
      <div class="navbar-header">
        <a class="navbar-brand" href="#">Collabrate</a>
      </div>
      <ul class="nav navbar-nav">
        <!-- template rendered iff not authed -->
          <li><router-link :to="{name:'login'}">Login</router-link></li>
          <li><router-link :to="{name:'register'}">Register</router-link></li>
      </ul>
    </div>
  </nav>
</template>

<script>
    export default {
      data() {
        return {
          isAuth: this.$auth.isAuthenticated()
        }
      },
      methods:{
        logout(){
          //destroys the loggined in user tokens 
          this.$auth.destroyToken();
          //check wheter the logout was success full
          if (!this.$auth.isAuthenticated()) {
            this.isAuth = this.$auth.isAuthenticated()
          }
          //makes a call to the router object 
          this.$router.push({name:"login"});
        }
      }
    }
</script>
