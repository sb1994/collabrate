<template lang="html">
  <div id="search">
    <loggedin-navbar></loggedin-navbar>
    <input type="text" id="search-box" v-model="searchText" v-on:keyup="getSelectedProjects()" placeholder="Search Project Term">
    <div class="row">
        <search-results v-for="project in projects" :project="project" :key="project.id"></search-results>
    </div>
  </div>
</template>

<script>
  import {apiDomain} from '../../config';
  import LoggedinNavBar from '../../components/LoggedinNavBar.vue';
  import SearchResults from './SearchResults.vue';
export default {

  data(){
    return{
      projects:[],
      searchText:'',
      categories:[],
      selectedCategory:''
    }
  },
  components:{
    //sets up the name of the tags that will be used in the current page
    'search-results':SearchResults,
    'loggedin-navbar':LoggedinNavBar
  },
  created(){
    this.path = apiDomain;
    axios.get(apiDomain+"api/getProjectCategories")
         .then(response=>{
          this.categories=response.data.categories;
         }).catch(function (error) {
          if (error.response) {
            console.log(error.response.data);
            console.log(error.response.status);
            console.log(error.response.headers);
          } else if (error.request) {
            // The request was made but no response was received
            // `error.request` is an instance of XMLHttpRequest in the browser
            console.log(error.request);
          } else {
            // Something happened in setting up the request that triggered an Error
            console.log('Error', error.message);
          }
          console.log(error.config);
        });
    axios.get(apiDomain+'api/getAllProjects')
      .then(response=>{
            //sets the projects in the model to the projects sent back in the ajax response 
            //for whent the component is first created  
            this.projects = response.data.projects;
            console.log(this.projects);
          })
          .catch(function (error) {
           if (error.response) {
             // The request was made and the server responded with a status code
             // that falls out of the range of 2xx
             console.log(error.response.data);
             console.log(error.response.status);
             console.log(error.response.headers);
           } else if (error.request) {
             // The request was made but no response was received
             console.log(error.request);
           } else {
             // Something happened in setting up the request that triggered an Error
             console.log('Error', error.message);
           }
           console.log(error.config);
         });
  },
  methods:{
    getSelectedProjects(){
    if(this.searchText.length > 1){
        axios.get(apiDomain+'api/getSelectedProjects/'+this.searchText)
        .then(response=>{
              this.projects = response.data.projects.data;
              //console.log(response.data);
              console.log(this.projects);
            }
        ).catch(function (error) {
           if (error.response) {
             // The request was made and the server responded with a status code
             // that falls out of the range of 2xx
             console.log(error.response.data);
             console.log(error.response.status);
             console.log(error.response.headers);
           } else if (error.request) {
             // The request was made but no response was received
             // `error.request` is an instance of XMLHttpRequest in the browser and an instance of
             // http.ClientRequest in node.js
             console.log(error.request);
           } else {
             // Something happened in setting up the request that triggered an Error
             console.log('Error', error.message);
           }
           console.log(error.config);
         });
      }else {
        axios.get(apiDomain+'api/getAllProjects/')
        .then(response=>{
              this.projects = response.data.projects;
              //console.log(response.data);
              console.log(this.projects);
            }
        ).catch(function (error) {
           if (error.response) {
             // The request was made and the server responded with a status code
             // that falls out of the range of 2xx
             console.log(error.response.data);
             console.log(error.response.status);
             console.log(error.response.headers);
           } else if (error.request) {
             // The request was made but no response was received
             // `error.request` is an instance of XMLHttpRequest in the browser and an instance of
             // http.ClientRequest in node.js
             console.log(error.request);
           } else {
             // Something happened in setting up the request that triggered an Error
             console.log('Error', error.message);
           }
           console.log(error.config);
         });
      }
    },
    getFilteredProjects(){
      if(this.searchText.length > 1 && this.selectedCategory !== ""){
        console.log("Project Term: " + this.searchText + " Selected category_id: " + selectedCategory);
        //   axios.get(apiDomain+'api/getSelectedProjects/'+this.searchText)
        //   .then(response=>{
        //         this.projects = response.data.projects.data;
        //         //console.log(response.data);
        //         console.log(this.projects);
        //       }
        //   ).catch(function (error) {
        //      if (error.response) {
        //        // The request was made and the server responded with a status code
        //        // that falls out of the range of 2xx
        //        console.log(error.response.data);
        //        console.log(error.response.status);
        //        console.log(error.response.headers);
        //      } else if (error.request) {
        //        // The request was made but no response was received
        //        // `error.request` is an instance of XMLHttpRequest in the browser and an instance of
        //        // http.ClientRequest in node.js
        //        console.log(error.request);
        //      } else {
        //        // Something happened in setting up the request that triggered an Error
        //        console.log('Error', error.message);
        //      }
        //      console.log(error.config);
        //    });
        // }else {
        //   axios.get(apiDomain+'api/getAllProjects/')
        //   .then(response=>{
        //         this.projects = response.data.projects;
        //         //console.log(response.data);
        //         console.log(this.projects);
        //       }
        //   ).catch(function (error) {
        //      if (error.response) {
        //        // The request was made and the server responded with a status code
        //        // that falls out of the range of 2xx
        //        console.log(error.response.data);
        //        console.log(error.response.status);
        //        console.log(error.response.headers);
        //      } else if (error.request) {
        //        // The request was made but no response was received
        //        // `error.request` is an instance of XMLHttpRequest in the browser and an instance of
        //        // http.ClientRequest in node.js
        //        console.log(error.request);
        //      } else {
        //        // Something happened in setting up the request that triggered an Error
        //        console.log('Error', error.message);
        //      }
        //      console.log(error.config);
        //    });
      }
  },
}
}
</script>

<style lang="css">
</style>
