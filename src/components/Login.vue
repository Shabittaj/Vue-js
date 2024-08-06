<template>
    <div>
        Login
        <hr/>
        <form @submit.prevent="loginForm">
        <label for="email">User Name</label>        
        <input type ="text" id="email" v-model="formData.email"><br>
        <label for="password">Password</label>        
        <input type ="text" id="password" v-model="formData.password"><br>
        <button>Login</button>
    </form>
    <div v-if="responseData">Response:
        <p>Message: {{ responseData.message }}</p>
        <p>Response: {{ responseData.response }}</p>
        <Home v-if="responseData.response == true"/>
    </div>
    </div>
</template>
<script>
import axios from 'axios';
import Home from './Home.vue';


export default {
    name: 'Login',
    data(){
        return{
        formData:{
            email:'',
            password:''
        },
        responseData:null,
        responseVal: false
    }
    },
    components:{
        Home
    },
    emits:{
        responsePage:''
    },
    methods:{
        async loginForm(){
            axios.post('http://localhost:5454/user/login',this.formData)
            .then(response=>this.responseData = response.data)
            .catch(error=>console.log(error.data));
            
        }
    }
}
</script>

<style lang="scss" scoped>

</style>