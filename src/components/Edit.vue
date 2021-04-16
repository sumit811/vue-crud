<template>
    <form v-on:submit="update">
      <table cellpadding="5" cellspacing="5" border="1">
        <tr>
            <td>Name</td>
            <td><input type="text" v-model="name"></td>
        </tr>
        <tr>
            <td>Username</td>
            <td><input type="text" v-model="username"></td>
        </tr>
        <tr>
            <td>Email</td>
            <td><input type="text" v-model="email"></td>
        </tr>
        <tr>
            <td><input type="submit" value="Update"></td>
            <td><router-link to="/">Back to Home</router-link> </td>
        </tr>
      </table>
    </form>
</template>

<script>
import Vue from 'vue'
import axios from 'axios'
import VueAxios from 'vue-axios'
Vue.use(VueAxios,axios);
export default {
  name: 'Edit',
  data(){
      return {
          id:'',
          name:'',
          username:'',
          email:''
      }
  },
  methods:{
    update:function(e){
      e.preventDefault();
       Vue.axios.put('http://localhost:3000/users/'+this.$route.params.userId,{name:this.name,username:this.username,email:this.email}).then((res) => {
        console.dir(res);
        return res.data;
    })
    }
  },
  mounted(){
    console.log('this.$route.params.id',this.$route.params.id);  
    Vue.axios.get('http://localhost:3000/users/'+this.$route.params.userId).then((res) => {
        console.dir(res);
        return res.data;
    }).then((data) => {
      this.id = data.id;
      this.name = data.name;
      this.username = data.username;
      this.email = data.email;
    });      
  }
}
</script>
