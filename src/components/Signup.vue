<template>
    <div>
        <!-- <pre>
            {{ JSON.stringify(formValues,null,2) }}
        </pre> -->
        Signup Page
        <hr/>
        <form @submit.prevent="submitForm">
        <label for="user-name">User Name </label>
        <input type="text" id="user-name" v-model="formValues.userName"><br>
        <label for="first-name">First Name </label>
        <input type="text" id="first-name" v-model="formValues.firstName"><br>
        <label for="last-name">Last Name </label>
        <input type="text" id="last-name" v-model="formValues.lastName"><br>
        <label for="email">Email </label>
        <input type="text" id="email" v-model="formValues.email"><br>
        <label for="password">Password </label>
        <input type="password" id="password" v-model="formValues.password"><br>
   
        <button>Submit</button>
    </form>

    <div v-if="responseData"><h4>Response Data:</h4>
            <p>Message: {{ responseData.message }}</p>
            <p>User Name: {{ responseData.userName }}</p></div>
    </div>
</template>

<script>
import axios, { Axios } from 'axios';

export default {
    name:'Signup',

    data(){
        return{
            formValues:{
                userName:'',
            firstName:'',
            lastName:'',
            email:'',
            password:''
            },
            responseData:null
        }
    },
    methods:{
        submitForm(){
            
            axios.post('http://localhost:5454/user/register',this.formValues)
            .then(response => this.responseData = response.data)
            .catch(error=>console.error(error))
            // console.log(this.responseData)
            this.formValues.email = ''
            this.formValues.firstName = ''
            this.formValues.lastName = ''
            this.formValues.password = ''
            this.formValues.userName= ''
        }
    }
}
</script>

<style scoped>

</style>