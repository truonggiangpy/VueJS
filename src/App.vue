<template>
  <div id="app">
<!-- //lọc dữ liệu sắp xếp tìm kiếm -->

    <containers
     v-bind:index_edit="index_edit"
      v-bind:form="form"
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
    ></containers>
    <modal
      v-bind:create_confirm_boolean="create_confirm_boolean"
      v-bind:evenremove="evenremove"
      v-on:Click_Create_table="Click_Create_table"
      v-on:Click_Cancel_table="Click_Cancel_table"
      v-on:removelineModle="removelineModle"
    ></modal>
    <modalLocDL
      v-show="isModalVisible"
      v-on:Confirm_Filter="Confirm_Filter"
      @close="closeModal"
    />
  </div>
</template>
<script>
import containers from './components/containers.vue'
import modal from './components/modal.vue'
import modalLocDL from './components/ModelLocDL.vue'
export default {
  name: 'App',
  components: {
    containers,
    modal,
    modalLocDL
  },
  data () {
    return {
      isModalVisible: false,
      index_edit: '',
      title: 'giang',
      create_confirm_boolean: '',
      evenremove: {},
      Temlate: '',
      Type: '',
      Company: '',
      VersionDate: '',
      ExpirationDate: '',
      Active: '',

      form: [
        // Temlate: this.Temlate,Type: this.Type, Company: this.Company,VersionDate: this.VersionDate, ExpirationDate: this.ExpirationDate, Active: this.Active
        {
          idfrom: '1111',
          Temlate: '133145-AFM-B6-TV-RADIOCOMMERCIALS-11-15 ',
          Type: 'Production',
          Company: 'Peptico',
          VersionDate: '17-12-2020',
          ExpirationDate: '17-12-2020',
          Active: 'Active',
          node1: 'Remove',
          node2: 'Edit'
        },
        {
          idfrom: '1112',
          Temlate: '13325243-AFM-B6-TV-RADIOCOMMERCIALS-11-15',
          Type: 'Production',
          Company: 'Peptico',
          VersionDate: '20-11-2020',
          ExpirationDate: '20-11-2020',
          Active: 'Active',
          node1: 'Remove',
          node2: 'Edit'
        },
        {
          idfrom: '1113',
          Temlate: '133352435-AFM-B6-TV-RADIOCOMMERCIALS-11-15',
          Type: 'Production',
          Company: 'Peptico',
          VersionDate: '20-11-2020',
          ExpirationDate: '20-11-2020',
          Active: 'Active',
          node1: 'Remove',
          node2: 'Edit'
        },
        {
          idfrom: '1114',
          Temlate: '1324-AFM-B6-TV-RADIOCOMMERCIALS-11-15',
          Type: 'Production',
          Company: 'Peptico',
          VersionDate: '20-11-2020',
          ExpirationDate: '20-11-2020',
          Active: 'Active',
          node1: 'Remove',
          node2: 'Edit'
        },
        {
          idfrom: '1115',
          Temlate: '1335-AFM-B6-TV-RADIOCOMMERCIALS-11-15',
          Type: 'Production',
          Company: 'Peptico',
          VersionDate: '20-11-2020',
          ExpirationDate: '20-11-2020',
          Active: 'Active',
          node1: 'Remove',
          node2: 'Edit'
        }
      ]
    }
  },
// ahihih test github
  methods: {
    // ChangeForm: function (form, formChange) {
    //   let Tem = []
    //   Tem = form
    //   form = formChange
    //   formChange = Tem
    // },

    check: function (formchange, string) {
      if (formchange.includes(string)) { return false } else return true
    },
    Confirm_Filter (e) {
      let formChange = this.form[0].Temlate
      formChange = formChange + 'haha'
      this.isModalVisible = e.isModalVisible
      alert(formChange)
      // let formChange2 = []
      // formChange2 = formChange

      // alert(this.formChange[0].Temlate)
      // alert(e.Temlate + e.Type + e.Company + e.VersionDate + e.Active)
      // let ob = {ahihi: 1}
      // if (e.Temlate !== '') {
      //   for (let i = formChange.length - 1; i >= 0; i--) {
      //     if (this.check(formChange[i].Temlate, e.Temlate)) {
      //       formChange.splice(i, 1)
      //     }
      //   }
      //   alert(formChange.length())
      // }
      // this.form = formChange
    },
    showModal () {
      this.isModalVisible = true
    },
    closeModal () {
      this.isModalVisible = false
    },
    convertDate: function (date, tt, type) {
      let ngay
      let thang
      let nam
      if (type === 'dd_mm_yyyy') {
        ngay = date.slice(0, 2)
        thang = date.slice(3, 5)
        nam = date.slice(6, 10)
        return nam + tt + thang + tt + ngay
      }
      if (type === 'yyyy_mm_dd') {
        nam = date.slice(0, 4)
        thang = date.slice(5, 7)
        ngay = date.slice(8, 10)
        return ngay + tt + thang + tt + nam
      }
    },
    random_number: function () {
      let random10019999 = 1
      let t = true
      while (t) {
        random10019999 = parseInt(Math.random() * (9999 - 1001) + 1001)
        let i = 0
        for (i = 0; i < this.form.length; i++) {
          if (String(random10019999) === this.form[i].idfrom) {
            break
          }
        }
        if (i < this.form.length - 1) t = true
        else t = false
      }
      return random10019999
    },

    // tạo bảng băng form
    Click_Create_table (e) {
      let i = 0
      let check = true
      e.ExpirationDate = this.convertDate(e.ExpirationDate, '-', 'yyyy_mm_dd')
      e.VersionDate = this.convertDate(e.VersionDate, '-', 'yyyy_mm_dd')
      e.idfrom = this.random_number()
      if (this.form.length === 0) { this.form[-1] = e }
      // if (this.form[this.form.length - 1].node2 !== 'Cancel') {
      //   this.form.push(e) // cập nhật lại giá trị form
      for (i = 0; i < this.form.length; i++) {
        if (this.form[i].node2 === 'Cancel_row' || this.form[i].node2 === 'Cancel') {
          check = false
        }
      }
      if (check) {
        this.form.push(e)
      } else {
        alert('Đang Tạo Bảng bằng dòng, hãy Bấm Cancel để quay lại')
      }
      this.form.Temlate = this.form.Temlate + ' '
      this.create_confirm_boolean = e.return_create_confirm_boolean
    },
    Click_Cancel_table (e) {
      this.create_confirm_boolean = e.return_create_confirm_boolean
    },
    changeevenn (e) {
      this.create_confirm_boolean = e.chuoi
      // console.log("apphihi"+ this.create_confirm_boolean)
      // this.$emit('changeeven',e)
    },

    // addfilter add table qua line
    addfilter (e) {
      let i = 0
      let check = true
      for (i = 0; i < this.form.length; i++) {
        if (this.form[i].node2 === 'Cancel_row' || this.form[i].node2 === 'Cancel') {
          check = false
        }
      }
      if (check) {
        e.idfrom = this.random_number()
        // alert(e.node1)
        this.form.push(e)
      }
    },
    FilterData (e) {
      this.isModalVisible = e
    },

    removeline (e) {
      this.evenremove = e
    },

    removelineModle (e) {
      let i = 0
      let index = 0
      let check = true
      for (i = 0; i < this.form.length; i++) {
        if (String(e.id) === String(this.form[i].idfrom)) {
          index = i
        }
        if (this.form[i].node2 === 'Cancel_row' || this.form[i].node2 === 'Cancel') {
          check = false
        }
      }
      if (check) {
        this.form.splice(index, 1)
        this.$emit('removeline', e)
      } else {
        alert('đang có trường xử lý')
      }
    },
    Cancel_AddFilter (e) {
      this.form.pop()
    },
    Cancel_Edit_row (e) {
      let i = 0
      let index = 0
      for (i = 0; i < this.form.length; i++) {
        if (e.idfrom === this.form[i].idfrom) {
          index = i
        }
      }
      this.form.splice(index, 1, this.form[-2])
    },
    Confirm_AddFilter (e) {
      e.ExpirationDate = this.convertDate(e.ExpirationDate, '-', 'yyyy_mm_dd')
      e.VersionDate = this.convertDate(e.VersionDate, '-', 'yyyy_mm_dd')
      this.form.splice(this.form.length - 1, 1, e)// thay thế phần từ cuối cùng
      // this.form.push(e)
      //   this.Temlate = "";
      //   this.Type = "";
      //   this.Company = "";
      //   this.VersionDate = "";
      //   this.ExpirationDate = "";
      //   this.Active = "";
    },
    Edit (e) {
      let i = 0
      let index = 0
      let check = true

      for (i = 0; i < this.form.length; i++) {
        if (String(e.idfrom) === String(this.form[i].idfrom)) {
          index = i
        }
        if (this.form[i].node2 === 'Cancel_row' || this.form[i].node2 === 'Cancel') {
          check = false
        }
      }

      if (check) {
        this.index_edit = index
        e.ExpirationDate = this.convertDate(e.ExpirationDate.trim(), '-', 'dd_mm_yyyy')
        e.VersionDate = this.convertDate(e.VersionDate.trim(), '-', 'dd_mm_yyyy')
        this.form[-2] = this.form[index]
        this.form.splice(index, 1, e)
      }
      this.form[-2].node2 = 'Edit'
    },
    Editline (e) {
      let i = 0
      let index = 0
      let check = true

      for (i = 0; i < this.form.length; i++) {
        if (String(e.idfrom) === String(this.form[i].idfrom)) { // cùng dữ liệu nếu không sẻ bị lỗi
          index = i
        }
        if (this.form[i].node2 === 'Cancel_row' || this.form[i].node2 === 'Cancel') {
          check = false
        }
      }

      if (check) {
        this.index_edit = index
        e.ExpirationDate = this.convertDate(e.ExpirationDate.trim(), '-', 'dd_mm_yyyy')
        e.VersionDate = this.convertDate(e.VersionDate.trim(), '-', 'dd_mm_yyyy')
        this.form[-2] = this.form[index]
        this.form.splice(index, 1, e)
      }
      this.form[-2].node2 = 'Edit'
    },
    Confirm_Edit (e) {
      let i = 0
      let index = 0
      e.ExpirationDate = this.convertDate(e.ExpirationDate, '-', 'yyyy_mm_dd')
      e.VersionDate = this.convertDate(e.VersionDate, '-', 'yyyy_mm_dd')
      for (i = 0; i < this.form.length; i++) {
        if (e.idfrom === this.form[i].idfrom) {
          index = i
        }
      }
      this.form.splice(index, 1, e)
    }
  }
}
</script>
<style>
#app {
  margin: 0px;
  padding: 0px;
  position: relative;
}
body {
  margin: 0px;
  padding: 0px;
  position: relative;
}
</style>
