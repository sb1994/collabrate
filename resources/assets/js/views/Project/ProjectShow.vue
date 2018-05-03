<template lang="html">
  <div>
<transition appear>
  <div id="project-view">

    <p>Id: {{project.id}}</p>
    <p>Project Name: {{project.name}}</p>
    <p>Project description: {{project.description}}</p>
      <!-- <p>{project.title}</p> -->
      <img v-bind:src='path + "/storage/img/cover_img/" + project.cover_img' class="img-responsive" alt="">
      <router-link :to="{name:'project_edit',params:{id:project.id}}" v-if="project.user_id ==this.$auth.getUserId()">Edit Project</router-link>
      <!-- <router-link :to="{name:'project_show',params:{id:project.id}}">Show Project</router-link> -->
      <!-- <pre>
        {{project}}
      </pre> -->
      <div class="row">
        <div class="col-md-12">
          <project-rating v-bind:project="project" v-on:updateProjectRating="updateProjectRating" ></project-rating>
          <project-comment-composer v-bind:projectId="project.id" v-on:commentAdded="updateCommentLog"></project-comment-composer>
          <project-comment-log v-bind:project_comments="project_comments"></project-comment-log>
          <!-- <pre>{{project}}</pre> -->
        </div>
      </div>
  </div>
</transition>
</div>
</template>

<script>
import {apiDomain} from '../../config';
import ProjectCommentLog from './Comments/ProjectCommentLog.vue';
import ProjectCommentComposer from './Comments/ProjectCommentComposer.vue';
import ProjectRating from './ProjectRating.vue';
export default {
  components:{
    'project-comment-log':ProjectCommentLog,
    'project-comment-composer':ProjectCommentComposer,
    'project-rating':ProjectRating
  },
  data(){
    return{
      project:{
        project_id:"",
        name:"",
        description:"",
        cover_img:"",
        user_id:"",
        noOfRating:"",
      },
      project_comments:[],
      path:apiDomain
    }
  },
  created(){
    //console.log(apiDomain+"api/getUserProject/"+this.project.project_id);
    axios.get(apiDomain+"api/getUserProject/"+this.$route.params.id)
        .then(response=>{
          this.project=response.data[0];
        }).catch(function (error) {
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
      axios.get(apiDomain+"api/getNoProjectRating/"+this.$route.params.id)
          .then(response=>{
              this.project.noOfRating = response.data.count;
              console.log('This is the Project Rating In the created function');
              
              console.log(this.project.noOfRating);
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
      axios.get(apiDomain+"api/getProjectCommentsByPid/"+this.$route.params.id)
        .then(response=>{
          this.project_comments=response.data.project_comments;
        }).catch(function (error) {
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
    },
    methods:{
      updateProjectRating(){
        axios.get(apiDomain+"api/getNoProjectRating/"+this.$route.params.id)
          .then(response=>{
              this.project.noOfRating = response.data.count;
              console.log('This is the Update Project Rating Function');
              
              console.log(this.project.noOfRating);
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
      },
      updateCommentLog(){
        axios.get(apiDomain+"api/getProjectCommentsByPid/"+this.$route.params.id)
             .then(response=>{
              //console.log(response.data[0]);
              this.project_comments=response.data.project_comments;
              //this.$router.push({name:"projects_view"});
              console.log(this.project_comments);
             }).catch(function (error) {
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
    }
  }
</script>

<style lang="css">
</style>
