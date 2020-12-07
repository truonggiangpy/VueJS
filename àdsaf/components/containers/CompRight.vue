<template>
<div id="container_right">
    <CompControl v-bind:form="form" v-on:changeeven="changeevenn"/>
    <CompTable v-bind:form="form"/>
  
       
</div>
</template>

<script>
import CompControl from './CompRight/CompControl.vue'
import CompTable from './CompRight/CompTable.vue'
export default {
  name: 'Contaiv',
  props: {
    form: Array,
   
  },
  data () {
    return {
      msg: ''
    }
  },
  
  components: {
      CompControl,
      CompTable
  },
  methods: {
    changeevenn(e) {
      
      this.$emit('changeeven',e)
    }
  }
}
</script>


<style scoped>
#container_right{

    height: 100vh;
	background: #a5acb1;
	padding:0px 10px;
    flex:1;
    display: flex;
    flex-direction: column;
}

</style>
