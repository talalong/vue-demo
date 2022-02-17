<template>
  <img alt="Vue logo" src="./assets/logo.png" />
  <child :parentValue="responseData" />
</template>

<script>

import Child from "./Child.vue"
import axios from 'axios'

export default {
  name: "App",
  
  data() {
    return {
      responseData: null    
    };
  },
  components: {
     Child
  },
  created (){
    this.lazyLoadData()
  },
  methods: {
    async lazyLoadData () {
      let response = await axios.get(`https://reqres.in/api/users?page=2`)
      this.responseData = response.data.data[0]
    }
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

</style>
