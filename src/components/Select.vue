<template>
    <table cellpadding="5" cellspacing="5" border="1">
        <tr>
            <th>Name</th>
            <th>Username</th>
            <th>Email</th>
            <th>Edit</th>
            <th>Delete</th>
        </tr>
        <tr v-for="user in users" :key="user.id">
            <td>{{ user.name }}</td>
            <td>{{ user.username }}</td>
            <td>{{ user.email }}</td>
            <td><router-link :to="{ path: 'edit/'+user.id}">Edit</router-link></td>
            <td><button type="button" v-on:click="deluser(user.id)">Delete</button> </td>
        </tr>
    </table>    
</template>
<script>
import Vue from 'vue';
import axios from 'axios';
import VueAxios from 'vue-axios';
Vue.use(VueAxios,axios);
export default {
    name:'Select',
    data(){
        return {
            users:null
        }
    },
    methods:{
        deluser: function(id){
            console.log('delete id',id);
            Vue.axios.delete('http://localhost:3000/users/'+id).then(() => {
                this.fetchUser(); 
            });
        },
        fetchUser: function(){
            Vue.axios.get('http://localhost:3000/users').then((res) => {
                this.users = res.data;
            });
        },
    },
    mounted(){
     this.fetchUser();   
    }
}
</script>
<style>
    table{
        width:800px;
        margin:auto;
    }
</style>   
