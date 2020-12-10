<template>
  <div id="container_right">
    <CompControl
      v-bind:formtam="formtam"
      v-on:addfilter="addfilter"
      v-on:changeeven="changeevenn"
      v-on:FilterData="FilterData"
      v-on:SearchData="SearchData"

    />
    <CompTable
       v-bind:index_edit="index_edit"
      v-bind:formtam="formtam"
      v-on:removeline="removeline"
      v-on:Cancel_AddFilter="Cancel_AddFilter"
      v-on:Confirm_AddFilter="Confirm_AddFilter"
      v-on:Editline="Editline"
      v-on:SortDL="SortDL"
      v-on:Edit="Edit"
      v-on:Confirm_Edit="Confirm_Edit"
      v-on:Cancel_Edit_row="Cancel_Edit_row"
    />
  </div>
</template>

<script>
import CompControl from './CompRight/CompControl.vue'
import CompTable from './CompRight/CompTable.vue'
export default {
  name: 'Contaiv',
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
    CompControl,
    CompTable
  },
  methods: {

    FilterData (e) {
      this.$emit('FilterData', e)
    },
    SearchData (e) {
      this.$emit('SearchData', e)
    },
    SortDL (e) {
      this.$emit('SortDL', e)
    },
    changeevenn (e) {
      this.$emit('changeeven', e)
    },
    addfilter (e) {
      this.$emit('addfilter', e)
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
    Editline (e) {
      this.$emit('Editline', e)
    },
    Edit (e) {
      this.$emit('Edit', e)
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

<style scoped>
#container_right {
  height: 100vh;
  background: #a5acb1;
  padding: 0px 10px;
  flex: 1;
  display: flex;
  flex-direction: column;
}
</style>
