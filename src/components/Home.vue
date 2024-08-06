<template>
    <div>
    <button @click="currentPage='CreateTask'">create task</button><br>
    <button @click="currentPage='ShowTask'" >show All Task</button><br>
    <button @click="currentPage='ShowTaskByDate'" >show task</button>
        <component :is="currentPage" />
    </div>
</template>

<script>
import CreateTask from './CreateTask.vue';
import ShowTask from './ShowTask.vue';
import ShowTaskByDate from './ShowTaskByDate.vue';


export default {
    name:'Home',
    data(){
        return{
            currentPage: 'ShowTask'
        }
    },
    components:{
        CreateTask,
        ShowTask,
        ShowTaskByDate
    },
   
    methods:{
        changePage(){
            this.currentPage=  this.currentPage === 'ShowTask' ? 'CreateTask' : 'ShowTask';
        },
        console(){
            alert('alert....')
        }
        },
    }

</script>

<style lang="scss" scoped>

</style>