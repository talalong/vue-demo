<template lang="pug">
multiselect(v-model="selectedValue" open-direction="bottom" :options="options" :loading="isLoading" @search-change="asyncFind" label="email" track-by="id" :internal-search="false")
div {{parentValue}}
</template>

<script>
import Multiselect from "vue-multiselect"
import axios from 'axios'
export default {
  name: "App",
  props:{
    parentValue: Object  
  },
  data() { 
    return {
      selectedValue: null,
      isLoading: false,
      options: [],
      fake_object: {'id': 123, 'email': 'faker@hehe.com'}
    };
  },
  components: {
     Multiselect
  },
  mounted (){
    this.selectedValue = this.parentValue
    console.log(this.parentValue);
  },
  methods:{
      async asyncFind () {
      this.isLoading = true
      let response = await axios.get(`https://reqres.in/api/users?page=2`)
      this.isLoading = false
      this.options = response.data.data
    },
  }
};
</script>

<style src="vue-multiselect/dist/vue-multiselect.css"></style>
