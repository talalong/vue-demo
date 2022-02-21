<template lang="pug">
child(:parentValue="responseData")
</template>

<script>

import Child from "./Child.vue"
import axios from 'axios'
export default {
  name: "Parent",
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
  }
};
</script>