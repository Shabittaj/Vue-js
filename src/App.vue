<template>
  <div>
    <!-- <button @click="togglePage()">{{ currentPage === 'Signup' ? 'Switch to Login' : 'Switch to Signup' }}</button> 
    <component :is="currentPage" />  -->
     <!-- <component :is="currentPage" @Signup = "currentPage='Login'" />-->


  <Home/>
  </div>
</template>

<script>

import Home from './components/Home.vue';
import Login from './components/Login.vue';
import Signup from './components/Signup.vue';

export default {
  components: {
    Login, 
    Signup,
    Home
    
  },
  data() {
    return {
      currentPage: 'Login' // Initially show Signup component
    };
  },
  methods: {
    togglePage() {
      this.currentPage = this.currentPage === 'Signup' ? 'Login' : 'Signup';
    }
  }
};
</script>

<style scoped>
/* Add scoped styles if necessary */
</style>
