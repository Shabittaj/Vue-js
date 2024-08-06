<template>
    <div>
        show task
        <hr/>
        <table>
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
    name:"ShowTask",
    data(){
        return{
            responseData:null
        }
    },
    created(){
        this.getDetails()
    },
    methods:{
        getDetails(){
            axios.get("http://localhost:5454/task/getAllTask")
            .then(Response=>this.responseData = Response.data)
            .catch(err=>console.error(err))
        }
    }
}
</script>

<style scoped>

</style>