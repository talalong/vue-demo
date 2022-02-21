<template lang="pug">
multiselect(
  v-model="selectedValue"
  :options="options"
  label="email"
  track-by="id"
  open-direction="bottom"
  )
p {{parentValue}}
p lol
</template>

<script>
import Multiselect from "vue-multiselect"
export default {
  name: "Child",
  props:{
    parentValue: Object  
  },
  data() { 
    return {
      selectedValue: null,
      options: [],
    };
  },
  components: {
     Multiselect
  },
  watch:{
    parentValue (value) {
      this.selectedValue = value
    }
  }
};
</script>

<style src="vue-multiselect/dist/vue-multiselect.css"></style>
