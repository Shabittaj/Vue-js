<template>
    <div>
        show Task by date
        <hr>
        <br/>
        <label for="date">Select date : </label>
        <input type="date" name="" id="date" v-model="date" @change="getDetails()"><br/>
        <br/>
        <hr>
        <table border v-if="responseData">
            <th>week</th>
            <th>date</th>
            <th>subject</th>
            <th>topic</th>
            <th>experiment</th>
             <tr v-for="data in responseData" :key="responseData.week">
                <td>{{ data.week }}</td>
                <td>{{ data.dateRange }}</td>
                <td>{{ data.subject }}</td>
                <td>{{ data.topic }}</td>
                <!-- <td><button @click=" data.filePath ">{{ data.fileName }}</button></td> -->
                <td><a :href="data.filePath" target="_blank">{{ data.fileName }}</a></td>
            </tr>

    </table>
    </div>
</template>

<script>
import axios from 'axios';

export default {
    name:'ShowTaskByDate',
    data(){
        return{
            date:'',
            responseData:null
        }
    },

    methods:{
        getDetails(){
            axios.get(`http://localhost:5454/task/getWithDate`,{
                params:  { date: this.date }
            })
            .then(Response=>this.responseData = Response.data)
            .catch(err=>console.error(err))
        }
    }

}
</script>

<style lang="scss" scoped>

</style>