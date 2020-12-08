<template>

  <div id="bang">

    <div class="flex-container">
      <div class="style col1" style="border-top-left-radius: 10px">
        Form ID#
      </div>
      <div class="style col2">TemPlate Name</div>
      <div class="style col3">Type</div>
      <div class="style col4">Company</div>
      <div class="style col5">Version Date</div>
      <div class="style col6">Expiration D</div>
      <div class="style col7">ACTIVE</div>
      <div class="style col8" style="border-top-right-radius: 10px"></div>
    </div>
            {{formChange}}
    <div id="tablefull">
      <div class="tdata">
        <div
          class="flex-container"
          v-for="user in formtam"
          :key="user"
          v-on:dblclick="Edit_Line"
        >
          <div class="col1">{{ user.idfrom }}</div>
          <div class="col2" v-if="user.node2 == 'Edit'">{{ user.Temlate }}</div>
          <div class="col2" v-else-if="user.node2 == 'Cancel'">
            <input
              v-on:keyup.esc="Cancel"
              v-on:keyup.enter="ConfirmEnter"
              style="width: 90%; flex-grow: 1"
              type="text"
              class="create"
              placeholder="Nhập Temlate"
              v-model="Temlate"
              name="Temlate_Name"
            />
          </div>
          <div class="col2" v-else-if="user.node2 == 'Cancel_row'">
            <input
              v-on:keyup.esc="Cancel_row"
              v-on:keyup.enter="ConfirmEnter_row"
              style="width: 90%; flex-grow: 1"
              type="text"
              class="create"
              placeholder="Nhập Temlate"
              v-model="formtam[index_edit].Temlate"
              name="Temlate_Name"
            />
          </div>
          <div class="col3" v-if="user.node2 == 'Edit'">{{ user.Type }}</div>
          <div class="col3" v-else-if="user.node2 == 'Cancel'">
            <select
              v-on:keyup.enter="ConfirmEnter"
              v-on:keyup.esc="Cancel"
              style="width: 90%"
              class="create"
              v-model="Type"
              id="type"
              name="type"
            >
              <option value="1">Payoll</option>
              <option value="2">Production</option>
            </select>
          </div>
          <div class="col3" v-else-if="user.node2 == 'Cancel_row'">
            <select
              v-on:keyup.enter="ConfirmEnter_row"
              v-on:keyup.esc="Cancel_row"
              style="width: 90%"
              class="create"
              v-model="formtam[index_edit].Type"
              id="type"
              name="type"
            >
              <option value="Payoll">Payoll</option>
              <option value="Production">Production</option>
            </select>
          </div>
          <div class="col4" v-if="user.node2 == 'Edit'">{{ user.Company }}</div>
          <div class="col3" v-else-if="user.node2 == 'Cancel'">
            <input
              v-on:keyup.enter="ConfirmEnter"
              v-on:keyup.esc="Cancel"
              style="width: 90%"
              v-model="Company"
              type="text"
              class="create"
              id="fname"
              placeholder="Nhập Conpany"
              name="Company"
            />
          </div>
          <div class="col3" v-else-if="user.node2 == 'Cancel_row'">
            <input
              v-on:keyup.enter="ConfirmEnter_row"
              v-on:keyup.esc="Cancel_row"
              style="width: 90%"
              v-model="formtam[index_edit].Company"
              type="text"
              class="create"
              id="fname"
              placeholder="Nhập Conpany"
              name="Company"
            />
          </div>
          <div class="col5" v-if="user.node2 == 'Edit'">
            {{ user.VersionDate }}
          </div>
          <div class="col3" v-else-if="user.node2 == 'Cancel'">
            <input
              v-on:keyup.enter="ConfirmEnter"
              v-on:keyup.esc="Cancel"
              style="width: 90%"
              v-model="VersionDate"
              type="date"
              class="create"
              id="myDate"
              value="0000-00-00"
            />
          </div>
          <div class="col3" v-else-if="user.node2 == 'Cancel_row'">
            <input
              v-on:keyup.enter="ConfirmEnter_row"
              v-on:keyup.esc="Cancel_row"
              style="width: 90%"
              v-model="formtam[index_edit].VersionDate"
              type="date"
              class="create"
              id="myDate"
              value="0000-00-00"
            />
          </div>
          <div class="col6" v-if="user.node2 == 'Edit'">
            {{ user.ExpirationDate }}
          </div>
          <div class="col3" v-else-if="user.node2 == 'Cancel'">
            <input
              v-on:keyup.enter="ConfirmEnter"
              v-on:keyup.esc="Cancel"
              style="width: 90%"
              v-model="ExpirationDate"
              type="date"
              class="create"
              id="myDate"
              value="0000-00-00"
            />
          </div>
          <div class="col3" v-else-if="user.node2 == 'Cancel_row'">
            <input
              v-on:keyup.enter="ConfirmEnter_row"
              v-on:keyup.esc="Cancel_row"
              style="width: 90%"
              v-model="formtam[index_edit].ExpirationDate"
              type="date"
              class="create"
              id="myDate"
              value="1999-02-10"
            />
          </div>
          <div class="col7" v-if="user.node2 == 'Edit'">{{ user.Active }}</div>
          <div class="col3" v-else-if="user.node2 == 'Cancel'">
            <select
              v-on:keyup.enter="ConfirmEnter"
              v-on:keyup.esc="Cancel"
              v-model="Active"
              style="width: 90%"
              class="create"
              id="country"
              name="country"
            >
              <option value="1">Active</option>
              <option value="2">Archive</option>
            </select>
          </div>
          <div class="col3" v-else-if="user.node2 == 'Cancel_row'">
            <select
              v-on:keyup.enter="ConfirmEnter_row"
              v-on:keyup.esc="Cancel_row"
              v-model="formtam[index_edit].Active"
              style="width: 90%"
              class="create"
              id="country"
              name="country"
            >
              <option value="Active">Active</option>
              <option value="Archive">Archive</option>
            </select>
          </div>
          <div
            class="col8"
            v-if="user.node2 == 'Edit'"
            style="text-align: center"
          >
            <a href="#" class="add" v-on:click="Edit">Edit</a>
            <a href="#id01" class="remove" v-on:click="remove">remove</a>
          </div>
          <div
            class="col8"
            v-else-if="user.node2 == 'Cancel'"
            style="text-align: center"
          >
            <a href="#" class="add" v-on:click="Confirm">Confirm</a>
            <a href="#" class="remove" v-on:click="Cancel">Cancel</a>
          </div>
          <div
            class="col8"
            v-else-if="user.node2 == 'Cancel_row'"
            style="text-align: center"
          >
            <a href="#" class="add" v-on:click="Confirm_row">Confirm</a>
            <a href="#" class="remove" v-on:click="Cancel_row">Cancel</a>
          </div>
        </div>
      </div>
      <div id="nextpage">
        <button class="nextpage" name="button" type="button">
          <a href="javascript:;" class="next"> &larr; </a>
        </button>
        <button class="nextpage" name="button" type="button">
          <a href="javascript:;" class="next"> &rarr; </a>
        </button>
      </div>

    </div>
  </div>
</template>
<script>
export default {
  name: 'bang',
  props: {
    formtam: Array[{}],
    index_edit: String
  },
  data () {
    return {
      form1: [],
      idform: '',
      Temlate: '',
      Type: '',
      Company: '',
      VersionDate: '',
      ExpirationDate: '',
      Active: ''

    }
  },

  // watch: {

  //   index_edit () {
  //     for (let i = 0; i <= this.form.length - 1; i++) {
  //       this.form1.push(this.form[i])
  //     }
  //     // alert('truoc khi xóa index: ' + i + this.form1)
  //     // this.form1.splice(0, 1)

  //     // if (this.check(formChange[i].Temlate, e.Temlate)) {
  //     //   formChange.splice(i, 1)
  //     // }

  //     alert(this.form1)
  //     // alert(this.formChange[0].Temlate)
  //     // if (e.Temlate !== '') {.
  //     for (let i = this.form.length - 1; i >= 0; i--) {
  //       if (this.form[i].Temlate.includes('1332')) {
  //       } else {
  //         this.form.splice(i, 1)
  //         alert(this.form1)
  //       }
  //     }
  //     //   this.$emit('input', this.form)
  //     // },
  //     // index_edit () {
  //     //   this.$emit('input', this.index_edit)
  //     // }
  //     // form () {
  //     //   this.formChange = this.form
  //     //   //this.form = []
  //     //   // alert(this.formChange[0].Temlate)
  //     // this.form1.splice(2, 1)
  //     // alert(this.form1)
  //   }
  // },

  computed: {
    //     formf: {
    //     this.index_edit ='dsf'
    //   for (let i = this.formChange.length - 1; i >= 0; i--) {
    //     if (this.check(this.formChange[i].Temlate, '1331')) {
    //       this.formChange.splice(i, 1)
    //     }
    //   }
    //   }
    //   return
    // }
    // // index_edit () {
    // //   this.$emit('input', this.index_edit)
    // // }
  },

  // eslint-disable-next-line no-dupe-keys
  methods: {
    giang: function () {
      this.users.push(this.formtam)
    },
    remove (e) {
      const elementtable = event.target.parentNode.parentNode.childNodes
      let getid = elementtable[0].innerHTML
      let getTemlate = elementtable[2].innerHTML
      let getType = elementtable[4].innerHTML
      let getCompany = elementtable[6].innerHTML
      let getVersionDate = elementtable[8].innerHTML
      let getExpirationDate = elementtable[10].innerHTML
      let getActive = elementtable[12].innerHTML
      let thaydoi = 'Remove'
      let data1 = {
        id: getid,
        Temlate: getTemlate,
        Type: getType,
        Company: getCompany,
        ExpirationDate: getExpirationDate,
        VersionDate: getVersionDate,
        Active: getActive,
        Change: thaydoi
      }
      this.$emit('removeline', data1)
    },
    Cancel (e) {
      let getidaddfilter = e.target.parentNode.parentNode.childNodes
      let id = getidaddfilter[0].innerHTML
      let DataAddfilter = {
        id: id
      }
      this.$emit('Cancel_AddFilter', DataAddfilter)
    },
    ConfirmEnter_row (e) {
      this.Confirm_row(e)
    },
    ConfirmEnter (e) {
      this.Confirm(e)
    },
    Confirm (e) {
      const lengthForm = e.target.parentNode.parentNode
      let Temlate = lengthForm.childNodes[2].childNodes[0].value.length
      let Type = lengthForm.childNodes[4].childNodes[0].value.length
      let Company = lengthForm.childNodes[6].childNodes[0].value.length
      let VersionDate = lengthForm.childNodes[8].childNodes[0].value.length
      let ExpirationDate = lengthForm.childNodes[10].childNodes[0].value.length
      let Active = lengthForm.childNodes[12].childNodes[0].value.length
      if (Temlate === 0 || Type === 0 || Company === 0 || VersionDate === 0 || ExpirationDate === 0 || Active === 0) {
        alert('Trường Dữ Liệu Chưa được nhập')
      } else {
        let getid = e.target.parentNode.parentNode.childNodes[0].innerHTML
        let type, Acti
        if (this.Type === '1') type = 'Payoll'
        if (this.Type === '2') type = 'Production'
        if (this.Active === '1') Acti = 'Active'
        if (this.Active === '2') Acti = 'Archive'
        let DataAddfilterC = {
          idfrom: getid,
          Temlate: this.Temlate,
          Type: type,
          Company: this.Company,
          VersionDate: this.VersionDate,
          ExpirationDate: this.ExpirationDate,
          Active: Acti,
          node1: 'Remove',
          node2: 'Edit'
        }
        this.$emit('Confirm_AddFilter', DataAddfilterC)
        // cập nhật rỗng cho các input khi them line mới
        this.idform = ''
        this.Temlate = ''
        this.Type = ''
        this.Company = ''
        this.VersionDate = ''
        this.ExpirationDate = ''
        this.Active = ''
      }
    },
    Confirm_row (e) {
      const lengthForm = e.target.parentNode.parentNode
      let Temlate = lengthForm.childNodes[2].childNodes[0].value.length
      let Type = lengthForm.childNodes[4].childNodes[0].value.length
      let Company = lengthForm.childNodes[6].childNodes[0].value.length
      let VersionDate = lengthForm.childNodes[8].childNodes[0].value.length
      let ExpirationDate = lengthForm.childNodes[10].childNodes[0].value.length
      let Active = lengthForm.childNodes[12].childNodes[0].value.length
      if (Temlate === 0 || Type === 0 || Company === 0 || VersionDate === 0 || ExpirationDate === 0 || Active === 0) {
        alert('Trường Dữ Liệu Chưa được nhập')
      } else {
        let getidaddfilterC = e.target.parentNode.parentNode.childNodes
        let id = getidaddfilterC[0].innerHTML
        let getTemlate = this.formtam[this.index_edit].Temlate

        let getType = this.formtam[this.index_edit].Type
        let getCompany = this.formtam[this.index_edit].Company
        let getVersionDate = this.formtam[this.index_edit].VersionDate
        let getExpirationDate = this.formtam[this.index_edit].ExpirationDate
        let getActive = this.formtam[this.index_edit].Active
        let DataAddfilterC = {
          idfrom: id,
          Temlate: getTemlate,
          Type: getType,
          Company: getCompany,
          VersionDate: getVersionDate,
          ExpirationDate: getExpirationDate,
          Active: getActive,
          node1: 'Remove',
          node2: 'Edit'
        }
        this.$emit('Confirm_Edit', DataAddfilterC)
        // cập nhật rỗng cho các input khi them line mới
        this.Temlate = ''
        this.Type = ''
        this.Company = ''
        this.VersionDate = ''
        this.ExpirationDate = ''
        this.Active = ''
      }
    },
    Cancel_row (e) {
      let getid = e.target.parentNode.parentNode.childNodes
      let id = getid[0].innerHTML
      let Data = {
        idfrom: id
      }
      this.$emit('Cancel_Edit_row', Data)
      // cập nhật rỗng cho các input khi them line mới
    },
    Edit (e) {
      let elementtable = event.target.parentNode.parentNode.childNodes
      let getid = elementtable[0].innerHTML
      let getTemlate = elementtable[2].innerHTML
      let getType = elementtable[4].innerHTML
      let getCompany = elementtable[6].innerHTML
      let getVersionDate = elementtable[8].innerHTML
      let getExpirationDate = elementtable[10].innerHTML
      let getActive = elementtable[12].innerHTML
      let data1 = {
        idfrom: getid,
        Temlate: getTemlate,
        Type: getType,
        Company: getCompany,
        ExpirationDate: getExpirationDate,
        VersionDate: getVersionDate,
        Active: getActive,
        node1: 'Confirm_row',
        node2: 'Cancel_row'
      }
      this.$emit('Edit', data1)
    },
    Edit_Line (e) {
      let elementtable = event.target.parentNode.childNodes
      let getid = elementtable[0].innerHTML
      let getTemlate = elementtable[2].innerHTML
      let getType = elementtable[4].innerHTML
      let getCompany = elementtable[6].innerHTML
      let getVersionDate = elementtable[8].innerHTML
      let getExpirationDate = elementtable[10].innerHTML
      let getActive = elementtable[12].innerHTML
      let data1 = {
        idfrom: getid,
        Temlate: getTemlate,
        Type: getType,
        Company: getCompany,
        ExpirationDate: getExpirationDate,
        VersionDate: getVersionDate,
        Active: getActive,
        node1: 'Confirm_row',
        node2: 'Cancel_row'
      }
      this.$emit('Editline', data1)
    }
  }
}
</script>
<style scoped>
.nextpage:hover {
  background: red;
  color: white;
}

#container_child {
  margin-left: 10px;
  margin-right: 10px;
}

#title {
  display: flex;
  justify-content: space-between;
  align-items: center;
  height: 40px;
}

.container2 {
  display: flex;
}

#content {
  margin: 20px;
  color: white;
}
table {
  border-collapse: collapse;
  height: 100%;
  background-color: rgb(167, 190, 119);
}

table tr:first-child th:first-child {
  border-top-left-radius: 15px;
  border: none;
}

table tr:first-child th:last-child {
  border-top-right-radius: 15px;
  border: none;
  background-attachment: fixed;
}

th {
  font-size: large;
  background-color: red;
  color: white;
}
td,
th {
  border: 1px solid #000000;
  text-align: left;
  padding: 15px;
}

a {
  text-decoration: none;
  color: white;
}

.tron {
  border-radius: 50%;
}
#content > div {
  padding: 5px;
}
.flex-container {
  min-width: 1100px;
  padding: 0px;
  margin: 0px;
  display: flex;
  line-height: 16px;
  background-color: rgb(255, 255, 255);
  border-top-right-radius: 10px;
  border-top-left-radius: 10px;
}
.flex-container > .style {
  background-color: rgb(255, 0, 0);
  font-size: 20px;
  flex: 1;
  padding: 10px;
  border: 1px solid black;
  color: white;
}

.flex-container > div {
  background-color: rgb(255, 255, 255);
  color: rgb(0, 0, 0);
  flex: 1;
  border: 1px solid black;
  padding: 10px;
  font-size: 10px;
}
.flex-container:first-child div:last-child {
  background-attachment: fixed;
  background-color: D0CFCF;
}

#bang {
  flex: 1;
  position: relative;
  border: 1px solid red;
  border-top-left-radius: 15px;
  border-top-right-radius: 15px;
  display: flex;

  flex-direction: column;
}
#tablefull {
  position: relative;
  height: 100%;
  width: 100%;
  flex: 1;
}
.tdata {
  position: absolute;
  overflow-y: overlay;
  height: 100%;
  width: 100%;
}
#Cancel_edit {
  font-size: 20px;
  color: red;
  margin-right: 5px;
  padding-right: 5px;
}

.nextpage {
  padding: 0px;
}
#nextpage {
  position: absolute;
  width: 100%;
  text-align: center;
  bottom: 25px;
  background-color: NONE;
  width: 40px;
  margin-left: 50%;
}
.next {
  color: black;
  background-color: rgb(255, 56, 56);
}

#container_child {
  display: flex;
  flex-direction: column;

  padding-bottom: 0;
}

.add {
  font-size: 20px;
  color: red;
  border-right: 1px solid black;
  margin-right: 5px;
  padding-right: 5px;
}
.add:hover {
  color: blue;
}
#Cancel_edit:hover {
  color: blue;
}
.remove {
  font-size: 20px;
  color: red;
  border-right: 1px solid black;
  margin-right: 5px;
  padding-right: 5px;
  border-right: none;
}
.remove:hover {
  color: blue;
}

.container {
  padding: 2px 16px;
}
.container1 {
  padding: 2px 16px;
  display: flex;
  justify-content: center;
}
.col1 {
  width: 10%;
}
.col2 {
  width: 30%;
}
.col3 {
  width: 10%;
}
.col4 {
  width: 10%;
}
.col5 {
  width: 10%;
}
.col6 {
  width: 10%;
}
.col7 {
  width: 10%;
}
.col8 {
  width: 10%;
}
</style>
