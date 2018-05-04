<template lang="html">
<div class="container">
		<!-- <loggedout-navbar></loggedout-navbar> -->
  <div class="row">
	  
    <div class="col-sm-8 col-lg-7"> 
		<small><h1 class="smallHeading">WELCOME TO COLLAB/RATE</h1></small>
		<h1>CREATE, <span class="designSpacing">DESIGN...</span> <br>GET INSPIRE!</h1>
		<span class="underline">...................................</span>
	  <p>Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500 Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500.</p>
	
		<button class="submit">Get Started!</button>
	  </div>
    
    <div class="col-sm-3 col-lg-4" >
	  
				
	  
	  </div>
	  <div class="col-sm-1 col-lg-1"></div>
  </div>
</div>
  
</template>

<script>
import LoggedoutNavBar from '../components/LoggedoutNavbar.vue';
export default {
// 	components:{
//     'loggedout-navbar':LoggedoutNavBar
//   },
	
}
</script>

<style lang="css">
.row{
			  
			  margin-top: 5%;
			  margin-bottom: 8.6%;
		  }
		  body {
			 background-image: linear-gradient(-225deg, #FF057C 0%, #8D0B93 50%, #321575 100%);
			  background-repeat: no-repeat;
			  background-size: cover;
			  font-size:16px;
			  line-height: 28px;
			  letter-spacing: .025rem;
			  
		  }
		  h1{
			  font-family: 'Roboto', sans-serif;
			  color: #fff;
			  font-weight: 600;
			  font-size: 6rem!important;
    			line-height: 7rem!important;
			   letter-spacing: .9rem;
		  }
		  
		  .smallHeading{
			  color: #fff;
			  font-size: 1.93rem!important;
    		line-height: 1.5rem!important;
			  
			  font-family: 'Montserrat', sans-serif;
		  }
		  
		  .designSpacing{
			  letter-spacing: 2rem;
			  
		  }
		  
		  .underline{
			
			  background-color: #ff1a56 !important;
			 
			  font-size: 12px;
			 
			  color:  #ff1a56 !important;
		  }
		  
		  p{
			  font-family: 'Open Sans', sans-serif;
			  font-size: 15px;
			  line-height: 30px;
			  color: #fff;
			  margin-top: 1%;
		  }
		  
		  .submit{

background-color: #000;
    border: none;
    color: white;
    padding: 15px 32px;
	
    text-align: center;
    text-decoration: none;
    display: inline-block;
    font-size: 16px;
	
	 transition: all 0.4s ease-in-out;

}

.submit:hover{

background-color: #222;
    border: none;
    color: white;
    padding: 15px 32px;
    text-align: center;
    text-decoration: none;
    display: inline-block;
    font-size: 16px;
	
	 transition: all 0.4s ease-in-out;

}
</style>
