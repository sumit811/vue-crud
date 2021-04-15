<template>
    <table cellpading="5" ceillspacing="5" border="1">
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
            <td><button type="button" on>Edit</button> </td>
            <td><button type="button">Delete</button> </td>
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
    mounted(){
        Vue.axios.get('http://localhost:3000/users').then((res) => {
            this.users = res.data;
            // return res.data;
            console.log(res);
        });
    }
}
</script>
<style>
    table{
        width:800px;
        margin:auto;
    }
</style>   
