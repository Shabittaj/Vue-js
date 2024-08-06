<template>
    <div>
      <!-- <pre>{{ JSON.stringify(formValue, null, 2) }}</pre> -->
      <h2>Create Task</h2>
      <hr />
      <form @submit.prevent="createTask">
        <label for="week">Week</label>
        <input type="number" v-model="formValue.week" /><br />
        <label for="dateRange">Date Range</label>
        <input type="text" v-model="formValue.dateRange" /><br />
        <label for="subject">Subject</label>
        <input type="text" v-model="formValue.subject" /><br />
        <label for="topic">Topic</label>
        <input type="text" v-model="formValue.topic" /><br />
        <label for="experiments">Experiments</label>
        <input type="file" @change="onFilePicked" /><br />
        <label for="from_date">From Date</label>
        <input type="date" v-model="formValue.fromDate"><br />
        <label for="to_date">To Date</label>
        <input type="date" v-model="formValue.toDate"><br />
        <button>Create Task</button>
      </form>
      <div v-if="responseData">response - week {{ responseData.week }} saved successfully</div>
    </div>
  </template>
  
  <script>
  import axios from 'axios';
  
  export default {
    name: "CreateTask",
    data() {
      return {
        formValue: {
          week: 0,
          fromDate:'',
          toDate: '',
          dateRange: '',
          subject: '',
          topic: '',
          experiments: null
        },
        responseData: null
      };
    },
    methods: {
      async createTask() {
        
        const formData = new FormData();
        formData.append('fromDate',this.formValue.fromDate);
        formData.append('toDate',this.formValue.toDate);
        formData.append('week', this.formValue.week);
        formData.append('dateRange', this.formValue.dateRange);
        formData.append('subject', this.formValue.subject);
        formData.append('topic', this.formValue.topic);
        if (this.formValue.experiments) {
          formData.append('experiments', this.formValue.experiments);
        }
  
        try {
          const response = await axios.post('http://localhost:5454/task/createTask', formData, {
            headers: {
              'Content-Type': 'multipart/form-data'
            }
          });
          this.responseData = response.data
        } catch (error) {
          console.error('Error creating task:', error);
        }
      },
      onFilePicked(event) {
        const file = event.target.files[0];
        this.formValue.experiments = file;
      }
    }
  };
  </script>
  
  <style scoped>
  /* Add your styles here */
  </style>
  