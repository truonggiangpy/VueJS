<template>
  <div class="app">
    <CompLeft></CompLeft>
    <CompRight
    v-bind:index_edit="index_edit"
      v-bind:formtam="formtam"
      v-on:changeeven="changeevenn"
      v-on:addfilter="addfilter"
      v-on:FilterData="FilterData"
      v-on:removeline="removeline"
      v-on:Cancel_AddFilter="Cancel_AddFilter"
      v-on:Confirm_AddFilter="Confirm_AddFilter"
      v-on:Editline="Editline"
      v-on:Edit="Edit"
      v-on:Confirm_Edit="Confirm_Edit"
      v-on:Cancel_Edit_row="Cancel_Edit_row"
    ></CompRight>

  </div>
</template>

<script>
import CompLeft from './containers/CompLeft.vue'
import CompRight from './containers/CompRight.vue'
export default {
  name: 'app',

  props: {
    formtam: Array,
    index_edit: String
  },
  data () {
    return {
      msg: ''
    }
  },
  components: {
    CompLeft,
    CompRight
  },
  methods: {
    changeevenn (e) {
      this.$emit('changeeven', e)
      // this.$emit('changeeven',e)
    },
    addfilter (e) {
      this.$emit('addfilter', e)
    },
    FilterData (e) {
      this.$emit('FilterData', e)
    },
    removeline (e) {
      this.$emit('removeline', e)
    },
    Cancel_AddFilter (e) {
      this.$emit('Cancel_AddFilter', e)
    },
    Confirm_AddFilter (e) {
      this.$emit('Confirm_AddFilter', e)
    },
    Edit (e) {
      this.$emit('Edit', e)
    },
    Editline (e) {
      this.$emit('Editline', e)
    },
    Confirm_Edit (e) {
      this.$emit('Confirm_Edit', e)
    },
    Cancel_Edit_row (e) {
      this.$emit('Cancel_Edit_row', e)
    }
  }
}
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
