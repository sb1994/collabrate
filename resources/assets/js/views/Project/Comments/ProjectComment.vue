<template lang="html">
  <div class="comment-box">
    <!-- <pre>{{project_comment}}</pre> -->
    <div class="comment-text">{{project_comment.comment}}</div>
    <div class="comment-footer">
        <div class="comment-info">
            <span class="comment-author">
                    <small> Comment By : {{user.name}}</small>
                </span>
				<hr>
            <!--<span class="comment-date">{{ project_comment.created_at}}</span>-->
        </div>
    </div>
  </div>
</template>

<script>
import {apiDomain} from '../../../config';
// import ProjectAction from './ProjectCommentActions.vue';

export default {
  props:['project_comment'],
  components:{
    //'project-action':ProjectAction
  },
  data(){
    return{
        user:[]
    }
  },
  mounted(){
    //console.log(apiDomain+"api/showProfile/"+this.project_comment.user_id);
    axios.get(apiDomain+"api/showProfile/"+this.project_comment.user_id)
    .then(response=>{
        this.user = response.data[0];
        //console.log(response.data);
        console.log(this.user);
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
  methods:{

  }
}
</script>

<style lang="css">
.comment .comment-text{
  color: #555f77;
  font-size: 15px;
  margin-bottom: 25px;
}

.comment .comment-footer{
  color: #acb4c2;
  font-size: 13px;
}

.comment .comment-footer:after{
  content: "";
  display: table;
  clear: both;
}

.comment .comment-footer a{
  color: #acb4c2;
  text-decoration: none;

  -webkit-transition: 350ms color;
  -moz-transition: 350ms color;
  -ms-transition: 350ms color;
  -o-transition: 350ms color;
  transition: 350ms color;
}

.comment .comment-footer a:hover{
  color: #555f77;
  text-decoration: underline;
}

.comment .comment-info{
  float: left;
  width: 85%;
}

.comment .comment-author{ }
.comment .comment-date{ }

.comment .comment-date:before{
  content: "|";
  margin: 0 10px;
}

.comment-actions{
  float: left;
  text-align: right;
  width: 15%;
}

.reply{
    margin-top: 5px;
    margin-left: 60px;
}
.list{
    list-style: none;
    list-style-type: none;
    display: inline !important;
}

</style>
