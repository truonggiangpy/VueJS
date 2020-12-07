<template>
  <div class="app">
    <CompLeft></CompLeft>
    <CompRight v-bind:form='form' v-on:changeeven="changeevenn"></CompRight>
    <div>{{ form.Temlate}}</div>
 
  </div>
</template>

<script>
import CompLeft from "./containers/CompLeft.vue";
import CompRight from "./containers/CompRight.vue";
export default {
  name: "app",

  props: {
    form: Array,
   
  },
  data() {
    return {
      msg: ""
    };
  },
  components: {
  CompLeft,
  CompRight
  },
    methods: {
    changeevenn(e) {
     this.$emit('changeeven',e)
      // this.$emit('changeeven',e)
    }
  }
};

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.app {
  display: flex;
  margin: 0px;
  padding: 0px;
  position: relative;
}
</style>
