<template>
    <form v-on:submit="add">
      <table cellpadding="5" cellspacing="5" border="1">
        <tr>
            <td>Name</td>
            <td><input type="text" v-model="name"> - <b>{{name}}</b></td>
        </tr>
        <tr>
            <td>Username</td>
            <td><input type="text" v-model="username"> - <b>{{username}}</b></td>
        </tr>
        <tr>
            <td>Email</td>
            <td><input type="text" v-model="email">- <b>{{email}}</b></td>
        </tr>
        <tr>
            <td><input type="submit" value="Submit"></td>
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
    name:'NewUserFrm',
    data() {
        return {
            name:'',
            username:'',
            email:''
        }
    },
    methods:{
        add:function(e){
            // console.log('eeeeee');
            e.preventDefault();
            const user = {name:this.name,username:this.username,email:this.email}
            console.log('newUser', user);
            Vue.axios.post('http://localhost:3000/users',user).then((res) => {
                console.log('res',res);
            })
        }
    }
}
</script>