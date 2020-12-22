<template>
  <div id="container_child">
    <div id="title">
      <div>
        <a href="javascript:;" style="color: blue">
          Dashboard &rsaquo; Contract Templates</a
        >
      </div>
      <div>
        <form
          class="example"
          action=""
          style="margin:auto; max-width:300px; display: flex; "
        >
          <input
            size="25"
            style="border-radius: 7px; outline: none  "
            type="text"
            placeholder="Search.."
          />
          <button style="width: 100px; " type="submit">Tìm Kiếm</button>
        </form>
      </div>
      <div>
        <form class="example" action="" style="margin:auto; max-width:300px; ">
          <button href="javascript:;" class="tron">^^</button>
          <button href="javascript:;" class="tron">*</button>
          <button href="javascript:;" class="tron">0</button>
        </form>
      </div>
    </div>
    <hr />
    <h1 id="container1">Contract Templates</h1>

    <div class="container2">
      <div style="color:blue">Union(8) &nbsp; &nbsp;</div>
      <div>Non-Union(12) &nbsp;</div>
      <div>MSA(3)</div>
    </div>
    <hr />
  </div>
</template>

<script>
export default {
  name: 'Control',
  data () {
    return {
      search: '',
      msg: '',
      Temlate: '',
      isModalVisible: 'true'
    }
  },
  watch: {
    search  () {
      this.$emit('SearchData', this.search)
    }
  },

  methods: {
    Handlechange (e) {
      var data = { chuoi: 'Create' }
      this.$emit('changeeven', data)
    },
    FilterData (e) {
      this.$emit('FilterData', this.isModalVisible)
    },

    // SortData (e) {
    //   this.$emit('SortData', this.isModalVisible)
    // },

    addtableline (e) {
      var data = {
        idfrom: '',
        Temlate: '',
        Type: '',
        Company: '',
        VersionDate: '',
        ExpirationDate: '',
        Active: '',
        node1: 'Confirm',
        node2: 'Cancel'
      }
      this.$emit('addfilter', data)
      this.Temlate = ''
      this.Type = ''
      this.Company = ''
      this.VersionDate = ''
      this.ExpirationDate = ''
      this.Active = ''
    }
  }
}

</script>
<style scoped>
.container2 {
  margin: 5px;
}
#control{
  display: flex;
  align-items: center;
}
#hahaserch {
  width: 600px;
  height: 30px;
  border: 2px solid blue;
  border-radius: 5px;

}
#container_child {
  display: flex;
  flex-direction: column;
  padding-bottom: 0;
}
#container_right {
  height: 100vh;
  background: #a5acb1;
  padding: 0px 10px;
  flex: 1;
  display: flex;
  flex-direction: column;
}
#title {
  display: flex;
  justify-content: space-between;
  align-items: center;
  height: 40px;
}

.container {
  padding: 2px 16px;
}

.container2 {
  display: flex;
}

.container1 {
  padding: 2px 16px;
  display: flex;
  justify-content: flex-end;
}
a {
  text-decoration: none;
  color: white;
}
</style>
