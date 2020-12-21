<template>
  <div id="app">
<!-- //lọc dữ liệu sắp xếp tìm kiếm -->
    <!-- <div>{{Loc}}</div> -->
    <containers
     v-bind:index_edit="index_edit"
      v-bind:formtam="formtam"
      v-bind:form="form"
      v-on:changeeven="changeevenn"
      v-on:addfilter="addfilter"
      v-on:FilterData="FilterData"
      v-on:SearchData="SearchData"
      v-on:SortDL="SortDL"
      v-on:backPage="backPage"
      v-on:nextPage="nextPage"
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
      changeSearch: '',
      index_edit: '',
      title: 'giang',
      create_confirm_boolean: '',
      evenremove: {},
      Temlate: 's',
      trang: 0,
      Type: '',
      Company: '',
      VersionDate: '',
      ExpirationDate: '',
      Active: 'dá',
      checkFilterData: 's',
      formtam: [],
      E: {},
      checkType_Sort: '',
      form: [
        // Temlate: this.Temlate,Type: this.Type, Company: this.Company,VersionDate: this.VersionDate, ExpirationDate: this.ExpirationDate, Active: this.Active
        {
          idfrom: '1115',
          Temlate: 'bahaha hihhi ',
          Type: 'Production',
          Company: 'Peptico',
          VersionDate: '17-12-2020',
          ExpirationDate: '17-12-2020',
          Active: 'Active',
          node1: 'Remove',
          node2: 'Edit'
        },
        {
          idfrom: '1113',
          Temlate: 'a3325243-AFM-B6-TV-RADIOCOMMERCIALS-11-15',
          Type: 'Production',
          Company: 'Haitico',
          VersionDate: '20-11-2020',
          ExpirationDate: '20-11-2020',
          Active: 'Archive',
          node1: 'Remove',
          node2: 'Edit'
        },
        {
          idfrom: '1111',
          Temlate: 'huhuhahahahaahahahaah',
          Type: 'Payoll',
          Company: 'Haitico',
          VersionDate: '25-12-2020',
          ExpirationDate: '20-11-2020',
          Active: 'Active',
          node1: 'Remove',
          node2: 'Edit'
        },
        {
          idfrom: '1114',
          Temlate: 'c324-AFM-B6-TV-RADIOCOMMERCIALS-11-15',
          Type: 'Production',
          Company: 'Peptico',
          VersionDate: '20-11-2020',
          ExpirationDate: '20-11-2020',
          Active: 'Active',
          node1: 'Remove',
          node2: 'Edit'
        },
        {
          idfrom: '1112',
          Temlate: '1999-AFM-B6-TV-RADIOCOMMERCIALS-11-15',
          Type: 'Payoll',
          Company: 'Peptico',
          VersionDate: '22-12-2020',
          ExpirationDate: '20-11-2020',
          Active: 'Archive',
          node1: 'Remove',
          node2: 'Edit'
        },
        {
          idfrom: '1117',
          Temlate: 'phan trang n',
          Type: 'Payoll',
          Company: 'Peptico',
          VersionDate: '22-12-2020',
          ExpirationDate: '20-11-2020',
          Active: 'Archive',
          node1: 'Remove',
          node2: 'Edit'
        },
        {
          idfrom: '1118',
          Temlate: 'phan trang n',
          Type: 'Payoll',
          Company: 'Peptico',
          VersionDate: '22-12-2020',
          ExpirationDate: '20-11-2020',
          Active: 'Archive',
          node1: 'Remove',
          node2: 'Edit'
        },
        {
          idfrom: '1119',
          Temlate: 'phan trang n',
          Type: 'Payoll',
          Company: 'Peptico',
          VersionDate: '22-12-2020',
          ExpirationDate: '20-11-2020',
          Active: 'Archive',
          node1: 'Remove',
          node2: 'Edit'
        }
      ]
    }
  },
  created () {
    for (let i = 0; i <= this.form.length - 1; i++) {
      this.formtam.push(this.form[i])
    }
  },
  computed: {// khi có data nào bên trong hàm thay đổi thì sẻ gọi gàm computed thực thi trả về cho computed

  },

  watch: {
    trang () {
      let lengthrow = this.form.length
      let indexPage = parseInt(lengthrow / 5)
      this.formtam = []
      let end
      alert(this.form.length - 1)
      if (indexPage === this.trang) { end = this.form.length - 1 } else {
        end = indexPage * 5 + 5
      }
      alert(end)
      for (let i = indexPage * 5; i < end; i++) {
        alert(this.formtam[i])
        this.formtam.push(this.form[i])
        // alert('phan tu form tam là: ' + this.formtam + ' phan tu của form' + this.form1)
      }
      // alert('day la form tam ' + this.formtam)
    },
    checkFilterData () {
      this.formtam = []
      for (let i = 0; i <= this.form.length - 1; i++) {
        this.formtam.push(this.form[i])
      }

      if (this.E.checkall === 'loc') {
        for (let i = this.formtam.length - 1; i >= 0; i--) {
          if (this.formtam[i].Temlate.includes(this.E.Temlate)) {
          } else {
            this.formtam.splice(i, 1)
          }
        }
        for (let i = this.formtam.length - 1; i >= 0; i--) {
          if (this.formtam[i].Type.includes(this.E.Type)) {
          } else {
            this.formtam.splice(i, 1)
          }
        }
        for (let i = this.formtam.length - 1; i >= 0; i--) {
          if (this.formtam[i].Company.includes(this.E.Company)) {
          } else {
            this.formtam.splice(i, 1)
          }
        }
        for (let i = this.formtam.length - 1; i >= 0; i--) {
          if (this.formtam[i].Active.includes(this.E.Active)) {
          } else {
            this.formtam.splice(i, 1)
          }
        }
        if (this.E.VersionDate !== '' && this.E.VersionDate[4] === '-') { this.E.VersionDate = this.convertDate(this.E.VersionDate, '-', 'yyyy_mm_dd') }
        for (let i = this.formtam.length - 1; i >= 0; i--) {
          if (this.formtam[i].VersionDate.includes(this.E.VersionDate)) {
          } else {
            this.formtam.splice(i, 1)
          }
        }
      } else {
      }
      this.checkFilterData = ''
    },
    changeSearch () {
      this.formtam = []
      for (let i = 0; i <= this.form.length - 1; i++) {
        this.formtam.push(this.form[i])
      }
      for (let i = this.formtam.length - 1; i >= 0; i--) {
        if (this.formtam[i].Temlate.includes(this.changeSearch)) {
        } else {
          this.formtam.splice(i, 1)
        }
      }
    }
  },

  methods: {
    check: function (formchange, string) {
      if (formchange.includes(string)) { return false } else return true
    },

    Confirm_Filter (e) {
      this.E = e
      this.checkFilterData = 'ahiis'
      this.isModalVisible = e.isModalVisible
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
      this.formtam = []
      for (let i = 0; i <= this.form.length - 1; i++) {
        this.formtam.push(this.form[i])
      }
    },
    Click_Cancel_table (e) {
      this.create_confirm_boolean = e.return_create_confirm_boolean
      this.formtam = []
      for (let i = 0; i <= this.form.length - 1; i++) {
        this.formtam.push(this.form[i])
      }
    },
    changeevenn (e) {
      this.create_confirm_boolean = e.chuoi
      // console.log("apphihi"+ this.create_confirm_boolean)
      // this.$emit('changeeven',e)
      this.formtam = []
      for (let i = 0; i <= this.form.length - 1; i++) {
        this.formtam.push(this.form[i])
      }
    },

    // addfilter add table qua line
    addfilter (e) {
      // alert(this.form)
      // if (this.formtam.length !== 0) {
      //   this.form = []
      //   for (let i = 0; i <= this.formtam.length - 1; i++) {
      //     this.form.push(this.formtam[i])
      //   }
      // }
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
        // if (this.formtam.length !== 0) {
        //   this.formtam.push(e)
        // }
      }
      this.formtam = []
      for (let i = 0; i <= this.form.length - 1; i++) {
        this.formtam.push(this.form[i])
      }
    },
    FilterData (e) {
      this.isModalVisible = e
      this.formtam = []
      for (let i = 0; i <= this.form.length - 1; i++) {
        this.formtam.push(this.form[i])
      }
    },
    SearchData (e) {
      this.changeSearch = e
    },
    SortDL (e) {
      this.formtam = []
      for (let i = 0; i <= this.form.length - 1; i++) {
        this.formtam.push(this.form[i])
      }
      switch (e.haha) {
        case 'Form ID#': for (let i = 0; i < this.formtam.length - 1; i++) { // buble sort
          for (let j = this.formtam.length - 1; j > 0; j--) {
            if (this.formtam[j].idfrom < this.formtam[ j - 1 ].idfrom) {
              let tam = {}
              tam = this.formtam[j]
              this.formtam[j] = this.formtam[ j - 1 ]
              this.formtam[ j - 1 ] = tam
            }
          }
        }
          break
        case 'Type':
          this.formtam.sort(function (a, b) {
            let titleA = a.Type.toLowerCase()
            let titleB = b.Type.toLowerCase()
            if (titleA < titleB) return -1
            if (titleA > titleB) return 1
            return 0
          })
          break
        case 'TemPlate Name':
          this.formtam.sort(function (a, b) {
            let titleA = a.Temlate.toLowerCase()
            let titleB = b.Temlate.toLowerCase()
            if (titleA < titleB) return -1
            if (titleA > titleB) return 1
            return 0
          })
          break
        case 'Company':
          this.formtam.sort(function (a, b) {
            let titleA = a.Company.toLowerCase()
            let titleB = b.Company.toLowerCase()
            if (titleA < titleB) return -1
            if (titleA > titleB) return 1
            return 0
          })
          break
        case 'ACTIVE':
          this.formtam.sort(function (a, b) {
            let titleA = a.Active.toLowerCase()
            let titleB = b.Active.toLowerCase()
            if (titleA < titleB) return -1
            if (titleA > titleB) return 1
            return 0
          })
          break
        case 'Version Date':
          this.formtam.sort(function (a, b) {
            a = a.VersionDate.toString().split('-')
            b = b.VersionDate.toString().split('-')
            return a[2] - b[2] || a[1] - b[1] || a[0] - b[0]
          })
          break
        case 'Expiration D':
          this.formtam.sort(function (a, b) {
            a = a.ExpirationDate.toString().split('-')
            b = b.ExpirationDate.toString().split('-')
            return a[2] - b[2] || a[1] - b[1] || a[0] - b[0]
          })
          break
      }
    },
    removeline (e) {
      this.evenremove = e
      this.formtam = []
      for (let i = 0; i <= this.form.length - 1; i++) {
        this.formtam.push(this.form[i])
      }
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
      this.formtam = []
      for (let i = 0; i <= this.form.length - 1; i++) {
        this.formtam.push(this.form[i])
      }
    },
    Cancel_AddFilter (e) {
      this.form.pop()
      this.formtam = []
      for (let i = 0; i <= this.form.length - 1; i++) {
        this.formtam.push(this.form[i])
      }
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
      this.formtam = []
      for (let i = 0; i <= this.form.length - 1; i++) {
        this.formtam.push(this.form[i])
      }
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
      this.formtam = []
      for (let i = 0; i <= this.form.length - 1; i++) {
        this.formtam.push(this.form[i])
      }
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
      this.formtam = []
      for (let i = 0; i <= this.form.length - 1; i++) {
        this.formtam.push(this.form[i])
      }
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
      this.formtam = []
      for (let i = 0; i <= this.form.length - 1; i++) {
        this.formtam.push(this.form[i])
      }
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
      this.formtam = []
      for (let i = 0; i <= this.form.length - 1; i++) {
        this.formtam.push(this.form[i])
      }
    },
    backPage (e) {
      this.trang = e.index - 1
    },
    nextPage (e) {
      this.trang = e.index
      alert(this.trang)
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
