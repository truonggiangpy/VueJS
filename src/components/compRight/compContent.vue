<template>
<div id="container">
    <div class="container2">
      <div id='control'>
        <div style="color:blue">
          <a
            @click="clickCreateTemp"
            id="Union"
            style="color: blue;"
            >+ Union Templates &nbsp; &nbsp;</a
          >
        </div>
        <div style="color:blue">
          <a @click="addTableLine" href="#" id="Filter" style="color: blue;"
            >Add Data &nbsp; &nbsp;</a
          >
        </div>
          <div style="color:blue">
          <a @click="filterData" href="#" id="FilterData" style="color: blue;"
            >Filter data &nbsp; &nbsp;</a
          >
        </div>
      </div>
      <div class="search-wrapper">
        <input id="hahaserch" type="text" v-model="search" placeholder="Search TemPlate Name"/>
      </div>
    </div>
    <div class="flex-container">
      <div @click="sortData" class="style col1" style="border-top-left-radius: 10px">Form ID# {{sortfor}}</div>
      <div class="style col2" @click="sortData">TemPlate Name {{sortTem}}</div>
      <div class="style col3" @click="sortData">Type {{sortTyp}}</div>
      <div class="style col4" @click="sortData">Company {{sortCom}}</div>
      <div class="style col5" @click="sortData">Version Date {{sortVer}}</div>
      <div class="style col6" @click="sortData">Expiration D {{sortExp}}</div>
      <div class="style col7" @click="sortData">ACTIVE {{sortACT}}</div>
      <div class="style col8" style="border-top-right-radius: 10px"></div>
    </div>
    <div id="tablefull">
      <div class="tdata">
        <div
          class="flex-container"
          v-for="(user,idx) in arrayTemtam"
          :key="idx"
          @dblclick="editLine"
        >
          <div class="col1">{{ user.idfrom }}</div>
          <div class="col2" v-if="user.node2 == 'Edit'">{{ user.Temlate }}</div>
          <div class="col2" v-else-if="user.node2 == 'Cancel'">
            <input
              @keyup.enter="confirmAddLine"
              @keyup.esc="cancelAddLine"
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
              @keyup.esc="cancelEdit"
              @keyup.enter="confirmEnter"
              style="width: 90%; flex-grow: 1"
              type="text"
              class="create"
              placeholder="Nhập Temlate"
              v-model="arrayTemtam[index_edit].Temlate"
              name="Temlate_Name"
            />
          </div>
          <div class="col3" v-if="user.node2 == 'Edit'">{{ user.Type }}</div>
          <div class="col3" v-else-if="user.node2 == 'Cancel'">
            <select
              @keyup.enter="confirmAddLine"
              @keyup.esc="cancelAddLine"
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
              @keyup.enter="confirmEnter"
              @keyup.esc="cancelEdit"
              style="width: 90%"
              class="create"
              v-model="arrayTemtam[index_edit].Type"
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
              @keyup.enter="confirmAddLine"
              @keyup.esc="cancelAddLine"
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
              @keyup.enter="confirmEnter"
              @keyup.esc="cancelEdit"
              style="width: 90%"
              v-model="arrayTemtam[index_edit].Company"
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
              @keyup.enter="confirmAddLine"
              @keyup.esc="cancelAddLine"
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
              @keyup.enter="confirmEnter"
              @keyup.esc="cancelEdit"
              style="width: 90%"
              v-model="arrayTemtam[index_edit].VersionDate"
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
              @keyup.enter="confirmAddLine"
              @keyup.esc="cancelAddLine"
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
              @keyup.enter="confirmEnter"
              @keyup.esc="cancelEdit"
              style="width: 90%"
              v-model="arrayTemtam[index_edit].ExpirationDate"
              type="date"
              class="create"
              id="myDate"
              value="1999-02-10"
            />
          </div>
          <div class="col7" v-if="user.node2 == 'Edit'">{{ user.Active }}</div>
          <div class="col3" v-else-if="user.node2 == 'Cancel'">
            <select
              @keyup.enter="confirmAddLine"
              @keyup.esc="cancelAddLine"
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
              @keyup.enter="confirmEnter"
              @keyup.esc="cancelEdit"
              v-model="arrayTemtam[index_edit].Active"
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
            id="dd"
            class="col8"
            v-if="user.node2 == 'Edit'"
            style="text-align: center"
          >
          <!-- <div class="dropup">
            <a @click="optionSetting" class="dropbtn">...</a>
             <div class="dropup-content">
              <a href="#home">Home</a>
              <a href="#about">About</a>
              <a href="#contact">Contact</a>
            </div>
          </div> -->
        <div class="dropup">
          <button class="dropbtn" @click="dropLeft" check="0">...</button>
          <div class="dropup-content">
            <button @click="edit">Edit</button>
            <button ><a style ="color: rgb(0, 0, 0)" @click="removeLine"  href="#id01">remove</a></button>
            <!-- <button>Link 3</button> -->
          </div>
        </div>
          </div>
          <div
            class="col8"
            v-else-if="user.node2 == 'Cancel'"
            style="text-align: center"
          >
            <a href="#" class="add" @click="confirmAddLine">Confirm</a>
            <a href="#" class="remove" @click="cancelAddLine">Cancel</a>
          </div>
          <div
            class="col8"
            v-else-if="user.node2 == 'Cancel_row'"
            style="text-align: center"
          >
            <a href="#" class="add" @click="confirmEdit">Confirm</a>
            <a href="#" class="remove" @click="cancelEdit">Cancel</a>
          </div>
        </div>
      </div>
      <div id="nextpage">
        <button class="nextpage" name="button" type="button " v-on:click="back">
          <a href="javascript:;" class="next"> &larr; </a>
        </button>
        <label>{{trang}}</label>
        <button class="nextpage" name="button" type="button" v-on:click="next">
          <a href="javascript:;" class="next"> &rarr; </a>
        </button>
      </div>
    </div>
    <compCreateUnion
     @confirmRemove="confirmRemove"
     @cancelRemove="cancelRemove"
     @createTem="createTem"
     @confirmCancel="confirmCancel"
     :confirmBoolean="confirmBoolean"
     :evenRemove="evenRemove"
     v-show="showModel"
    />
    <compFilter
    @confirmFilter="confirmFilter"
    @closeFilter="closeFilter"
    @allData="allData"
    v-show="showFilter"
    />
  </div>

</template>
<script>
import compCreateUnion from './compCreateUnion.vue'
import compFilter from './compFilter.vue'
export default {
  name: 'container',
  components: {
    compCreateUnion,
    compFilter
  },
  props: {
    // index_edit: String
  },
  data () {
    return {
      evenRemove: {},
      trangtam: '',
      trang: 1,
      showFilter: false,
      showModel: false,
      typeSort: 'up',
      confirmBoolean: '',
      index_edit: '',
      idarrayTem: '',
      Temlate: '',
      Type: '',
      Company: '',
      VersionDate: '',
      ExpirationDate: '',
      sortfor: '',
      sortTem: '',
      sortTyp: '',
      sortCom: '',
      sortVer: '',
      sortExp: '',
      sortACT: '',
      Active: '',
      search: '',
      searchtam: [],
      checkSearchtam: false,
      arrayTemtam: [],
      arrayTem: [
        // Temlate: this.Temlate,Type: this.Type, Company: this.Company,VersionDate: this.VersionDate, ExpirationDate: expirationDate, Active: this.Active
        {
          idfrom: '1101',
          Temlate: 'vahaha hihhi ',
          Type: 'Production',
          Company: 'Peptico',
          VersionDate: '17-12-2020',
          ExpirationDate: '17-12-2020',
          Active: 'Active',
          node1: 'Remove',
          node2: 'Edit'
        },
        {
          idfrom: '1102',
          Temlate: 'cahaha hihhi ',
          Type: 'Production',
          Company: 'Peptico',
          VersionDate: '18-12-2020',
          ExpirationDate: '17-12-2020',
          Active: 'Active',
          node1: 'Remove',
          node2: 'Edit'
        },
        {
          idfrom: '1103',
          Temlate: 'aahaha hihhi ',
          Type: 'Production',
          Company: 'Peptico',
          VersionDate: '13-12-2020',
          ExpirationDate: '17-12-2020',
          Active: 'Active',
          node1: 'Remove',
          node2: 'Edit'
        },
        {
          idfrom: '1104',
          Temlate: 'uuuhaha hihhi ',
          Type: 'Production',
          Company: 'Peptico',
          VersionDate: '12-12-2020',
          ExpirationDate: '17-12-2020',
          Active: 'Active',
          node1: 'Remove',
          node2: 'Edit'
        },
        {
          idfrom: '1105',
          Temlate: 'kkkaha hihhi ',
          Type: 'Production',
          Company: 'Peptico',
          VersionDate: '11-12-2020',
          ExpirationDate: '17-12-2020',
          Active: 'Active',
          node1: 'Remove',
          node2: 'Edit'
        },
        {
          idfrom: '1106',
          Temlate: 'mmmaha hihhi ',
          Type: 'Production',
          Company: 'Peptico',
          VersionDate: '17-12-2020',
          ExpirationDate: '17-12-2020',
          Active: 'Active',
          node1: 'Remove',
          node2: 'Edit'
        },
        {
          idfrom: '1107',
          Temlate: 'nnnaha hihhi ',
          Type: 'Production',
          Company: 'Peptico',
          VersionDate: '22-12-2020',
          ExpirationDate: '17-12-2020',
          Active: 'Active',
          node1: 'Remove',
          node2: 'Edit'
        },
        {
          idfrom: '1108',
          Temlate: 'ooaha hihhi ',
          Type: 'Production',
          Company: 'Peptico',
          VersionDate: '21-12-2020',
          ExpirationDate: '17-12-2020',
          Active: 'Active',
          node1: 'Remove',
          node2: 'Edit'
        },
        {
          idfrom: '1109',
          Temlate: 'a3325243-AFM-B6-TV-RADIOCOMMERCIALS-11-15',
          Type: 'Production',
          Company: 'Haitico',
          VersionDate: '24-11-2020',
          ExpirationDate: '20-11-2020',
          Active: 'Archive',
          node1: 'Remove',
          node2: 'Edit'
        },
        {
          idfrom: '1110',
          Temlate: 'xxuhahahahaahahahaah',
          Type: 'Payoll',
          Company: 'Haitico',
          VersionDate: '25-12-2020',
          ExpirationDate: '20-11-2020',
          Active: 'Active',
          node1: 'Remove',
          node2: 'Edit'
        },
        {
          idfrom: '1111',
          Temlate: 'c324-AFM-B6-TV-RADIOCOMMERCIALS-11-15',
          Type: 'Production',
          Company: 'Peptico',
          VersionDate: '26-11-2020',
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
          VersionDate: '27-12-2020',
          ExpirationDate: '20-11-2020',
          Active: 'Archive',
          node1: 'Remove',
          node2: 'Edit'
        }
      ]
    }
  },
  created () {
    for (let i = 0; i < 5; i++) {
      this.arrayTemtam.push(this.arrayTem[i])
    }
    history.pushState(null, null, 'Home')
  },
  computed: {

  },
  watch: {
    search () {
      if (this.search.length !== 0) {
        history.pushState(null, null, 'search=' + this.search)
        this.checkSearchtam = true
      } else {
        history.pushState(null, null, 'Home')
        this.checkSearchtam = false
      }
      this.searchtam = []
      for (let [i] of this.arrayTem.entries()) {
        this.searchtam.push(this.arrayTem[i])
      }
      for (let i = this.searchtam.length - 1; i >= 0; i--) {
        if (this.searchtam[i].Temlate.includes(this.search)) {
        } else {
          this.searchtam.splice(i, 1)
        }
      }
      this.trangtam = 1
      this.trang = -10
    },
    trang () {
      if (this.trang < 0) {
        this.trang = this.trangtam
      }
      // let lengthrow = this.arrayTem.length
      // let indexPage = parseInt(lengthrow / 5)
      this.arrayTemtam = []
      // let end
      let trangtam = 5 * (this.trang)
      // if (indexPage === this.trang) { end = this.arrayTem.length - 1 } else {
      //   end = indexPage * 5 + 5
      // }
      let endArray
      if (this.checkSearchtam === true) {
        if (trangtam > this.searchtam.length) endArray = this.searchtam.length
        else endArray = trangtam
        // if (trangtam === this.arrayTem.length / 5) {
        for (let i = trangtam - 5; i < endArray; i++) {
          this.arrayTemtam.push(this.searchtam[i])
        }
      } else {
        if (trangtam > this.arrayTem.length) endArray = this.arrayTem.length
        else endArray = trangtam
        // if (trangtam === this.arrayTem.length / 5) {
        for (let i = trangtam - 5; i < endArray; i++) {
          this.arrayTemtam.push(this.arrayTem[i])
        }
      }
    }
  },
  methods: {
    back (e) {
      // let indexPage
      // let lengthrow = this.arrayTem.length
      // if (lengthrow % 5 !== 0) {
      //   indexPage = parseInt(lengthrow / 5)
      // } else {
      //   indexPage = parseInt(lengthrow / 5) - 1
      // }
      this.trang = this.trang - 1
      if (this.trang < 1) {
        this.trang = 1
      }
      history.pushState(null, null, 'page' + this.trang)
    },
    next (e) {
      let indexPage
      let lengthrow = this.arrayTem.length
      if (lengthrow % 5 !== 0) {
        indexPage = parseInt(lengthrow / 5)
      } else {
        indexPage = parseInt(lengthrow / 5) - 1
      }
      this.trang = this.trang + 1
      if (this.trang > indexPage) {
        this.trang = indexPage + 1
      }
      history.pushState(null, null, 'page' + this.trang)
    },
    edit (event) {
      history.pushState(null, null, 'edit')
      let elementtable = event.target.parentNode.parentNode.parentNode.parentNode.childNodes
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
      let index = 0
      let check = true
      for (let [i, v] of this.arrayTem.entries()) {
        if (String(data1.idfrom) === String(v.idfrom)) {
          index = i
        }
        if (v.node2 === 'Cancel_row' || v.node2 === 'Cancel') {
          check = false
        }
      }
      if (check) {
        this.index_edit = index % 5
        data1.ExpirationDate = this.convertDate(data1.ExpirationDate.trim(), '-', 'dd_mm_yyyy')
        data1.VersionDate = this.convertDate(data1.VersionDate.trim(), '-', 'dd_mm_yyyy')
        this.arrayTem[-2] = this.arrayTem[index]
        this.arrayTem.splice(index, 1, data1)
      }
      this.arrayTem[-2].node2 = 'Edit'
      this.dropLeft(event.target.parentNode.parentNode.childNodes[0])
      // this.arrayTemtam = []

      // for (let [i, v] of this.arrayTem.entries()) {
      //   this.arrayTemtam.push(v)
      //   alert(this.arrayTemtam[i].idform)
      // }
      // this.arrayTemtam = []
      this.trangtam = this.trang
      this.trang = -10
    },
    confirmEdit (e) {
      const lengtharrayTem = e.target.parentNode.parentNode
      let Temlate = lengtharrayTem.childNodes[2].childNodes[0].value.length
      if (Temlate === 0) {
        alert('Trường Dữ Liệu Chưa được nhập')
      } else {
        let getidaddfilterC = e.target.parentNode.parentNode.childNodes
        let id = getidaddfilterC[0].innerHTML
        let getTemlate = this.arrayTemtam[this.index_edit].Temlate
        let getType = this.arrayTemtam[this.index_edit].Type
        let getCompany = this.arrayTemtam[this.index_edit].Company
        let getVersionDate = this.arrayTemtam[this.index_edit].VersionDate
        let getExpirationDate = this.arrayTemtam[this.index_edit].ExpirationDate
        let getActive = this.arrayTemtam[this.index_edit].Active
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
        let index = 0
        DataAddfilterC.ExpirationDate = this.convertDate(DataAddfilterC.ExpirationDate, '-', 'yyyy_mm_dd')
        DataAddfilterC.VersionDate = this.convertDate(DataAddfilterC.VersionDate, '-', 'yyyy_mm_dd')
        // for (i = 0; i < this.arrayTem.length; i++) {
        //   if (DataAddfilterC.idfrom === this.arrayTem[i].idfrom) {
        //     index = i
        //   }
        // }
        // for (let i in this.arrayTem) {
        //   if (DataAddfilterC.idfrom === this.arrayTem[i].idfrom) {
        //     index = i
        //   }
        // }
        this.arrayTem.forEach((v, i) => { // foreach duyetj từ 0 - length
          if (DataAddfilterC.idfrom === this.arrayTem[i].idfrom) {
            index = i
          }
        })
        this.arrayTem.splice(index, 1, DataAddfilterC)
        this.arrayTemtam = []
        this.trangtam = this.trang
        this.trang = -10
        // for (let i in this.arrayTem) {
        //   this.arrayTemtam.push(this.arrayTem[i])
        // }
        // for (const v of this.arrayTem) {
        //   this.arrayTemtam.push(v)
        // }
        // this.arrayTem.forEach((v, i) => // foreach duyetj từ 0 - length
        //   this.arrayTemtam.push(v)
        // )
        // for (let i = 0; i <= this.arrayTem.length - 1; i++) {
        //   this.arrayTemtam.push(this.arrayTem[i])
        // }
      }
      // cập nhật rỗng cho các input khi them line mới
      this.Temlate = ''
      this.Type = ''
      this.Company = ''
      this.VersionDate = ''
      this.expirationDate = ''
      this.Active = ''
    },
    cancelEdit (e) {
      let getid = e.target.parentNode.parentNode.childNodes
      let id = getid[0].innerHTML
      let Data = {
        idfrom: id
      }

      let index = 0
      for (let [i] of this.arrayTem.entries()) {
        if (Data.idfrom === this.arrayTem[i].idfrom) {
          index = i
        }
      }
      this.arrayTem.splice(index, 1, this.arrayTem[-2])
      // this.arrayTemtam = []
      // for (let v of this.arrayTem) {
      //   this.arrayTemtam.push(v)
      // }
      this.trangtam = this.trang
      this.trang = -10
      // for (let i = 0; i <= this.arrayTem.length - 1; i++) {
      //   this.arrayTemtam.push(this.arrayTem[i])
      // }
    },
    editLine (e) {
      history.pushState(null, null, 'editLine')
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
      let index = 0
      let check = true

      for (let [i] of this.arrayTem.entries()) {
        if (String(data1.idfrom) === String(this.arrayTem[i].idfrom)) { // cùng dữ liệu nếu không sẻ bị lỗi
          index = i
        }
        if (this.arrayTem[i].node2 === 'Cancel_row' || this.arrayTem[i].node2 === 'Cancel') {
          check = false
        }
      }
      if (check) {
        this.index_edit = index % 5
        data1.ExpirationDate = this.convertDate(data1.ExpirationDate.trim(), '-', 'dd_mm_yyyy')
        data1.VersionDate = this.convertDate(data1.VersionDate.trim(), '-', 'dd_mm_yyyy')
        this.arrayTem[-2] = this.arrayTem[index]
        this.arrayTem.splice(index, 1, data1)
      }
      this.arrayTem[-2].node2 = 'Edit'
      // this.arrayTemtam = []
      // for (let v of this.arrayTem) {
      //   this.arrayTemtam.push(v)
      // }
      this.trangtam = this.trang
      this.trang = -10
    },
    removeLine (e) {
      this.showModel = true
      const elementtable = event.target.parentNode.parentNode.parentNode.parentNode.parentNode.childNodes
      let getid = elementtable[0].innerHTML
      let getTemlate = elementtable[2].innerHTML
      let getType = elementtable[4].innerHTML
      let getCompany = elementtable[6].innerHTML
      let getVersionDate = elementtable[8].innerHTML
      let getExpirationDate = elementtable[10].innerHTML
      let getActive = elementtable[12].innerHTML
      let thaydoi = 'Remove'
      this.dropLeft(event.target.parentNode.parentNode.parentNode.childNodes[0])
      this.confirmBoolean = 'Remove'
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
      this.evenRemove = data1
    },
    confirmRemove (e) {
      this.showModel = false
      let index = 0
      let check = true
      for (let [i] of this.arrayTem.entries()) {
        if (String(e.id) === String(this.arrayTem[i].idfrom)) {
          index = i
        }
        if (this.arrayTem[i].node2 === 'Cancel_row' || this.arrayTem[i].node2 === 'Cancel') {
          check = false
        }
      }
      if (this.search.length !== 0) {
        for (let [i] of this.searchtam.entries()) {
          if (String(e.id) === String(this.searchtam[i].idfrom)) {
            this.searchtam.splice(i, 1)
          }
        }
      }
      if (check) {
        this.arrayTem.splice(index, 1)
        this.$emit('removeline', e)
      } else {
        alert('đang có trường xử lý')
      }
      this.trangtam = this.trang
      this.trang = -10
      // this.arrayTemtam = []
      // for (let v of this.arrayTem) {
      //   this.arrayTemtam.push(v)
      // }
    },
    cancelRemove (e) {
      this.showModel = e
    },
    clickCreateTemp (e) {
      history.pushState(null, null, 'Create')
      this.checkSearchtam = false
      this.showModel = true
      this.confirmBoolean = 'Create'
      // console.log("apphihi"+ this.create_confirm_boolean)
      // this.$emit('changeeven',e)
      this.arrayTemtam = []
      this.trangtam = this.trang
      this.trang = -10
    },
    createTem (e) {
      history.pushState(null, null, 'Home')
      this.showModel = false
      let check = true
      e.ExpirationDate = this.convertDate(e.ExpirationDate, '-', 'yyyy_mm_dd')
      e.VersionDate = this.convertDate(e.VersionDate, '-', 'yyyy_mm_dd')
      e.idfrom = this.randomNumber()
      if (this.arrayTem.length === 0) { this.arrayTem[-1] = e }
      // if (this.arrayTem[this.arrayTem.length - 1].node2 !== 'Cancel') {
      //   this.arrayTem.push(e) // cập nhật lại giá trị arrayTem
      for (let [i] of this.arrayTem.entries()) {
        if (this.arrayTem[i].node2 === 'Cancel_row' || this.arrayTem[i].node2 === 'Cancel') {
          check = false
        }
      }
      if (check) {
        this.arrayTem.push(e)
      } else {
        alert('Đang Tạo Bảng bằng dòng, hãy Bấm Cancel để quay lại')
      }
      this.arrayTem.Temlate = this.arrayTem.Temlate + ' '
      this.create_confirm_boolean = e.return_create_confirm_boolean
      this.arrayTemtam = []
      this.trang = -10
    },
    confirmEnter (e) {
      this.confirmEdit(e)
    },
    confirmCancel (e) { // dùng để xác nhận cancel khi đang tạo teamplate
      history.pushState(null, null, 'Home')
      this.showModel = false
    },
    addTableLine (e) {
      history.pushState(null, null, 'addLine')
      this.checkSearchtam = false
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
      let check = true
      for (let [i] of this.arrayTem.entries()) {
        if (this.arrayTem[i].node2 === 'Cancel_row' || this.arrayTem[i].node2 === 'Cancel') {
          check = false
        }
      }
      let indexAddLine = this.trang * 5 - 1
      if (check) {
        data.idfrom = this.randomNumber()
        this.arrayTem.splice(indexAddLine, 0, data)
      }
      // this.arrayTemtam = []
      // for (let [, v] of this.arrayTem.entries()) {
      //   this.arrayTemtam.push(v)
      // }
      this.trangtam = this.trang
      this.trang = -10
      this.Temlate = ''
      this.Type = ''
      this.Company = ''
      this.VersionDate = ''
      this.expirationDate = ''
      this.Active = ''
    },
    confirmAddLine (e) {
      history.pushState(null, null, 'Home')
      const lengtharrayTem = e.target.parentNode.parentNode
      let Temlate = lengtharrayTem.childNodes[2].childNodes[0].value.length
      if (Temlate === 0) {
        alert('Trường Tamplate chưa được nhập')
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
          ExpirationDate: this.expirationDate,
          Active: Acti,
          node1: 'Remove',
          node2: 'Edit'
        }
        DataAddfilterC.ExpirationDate = this.convertDate(DataAddfilterC.ExpirationDate, '-', 'yyyy_mm_dd')
        DataAddfilterC.VersionDate = this.convertDate(DataAddfilterC.VersionDate, '-', 'yyyy_mm_dd')
        let idform = e.target.parentNode.parentNode.childNodes[0].innerHTML
        for (let [i] of this.arrayTem.entries()) {
          if (String(this.arrayTem[i].idfrom) === idform) {
            this.arrayTem.splice(i, 1, DataAddfilterC)// thay thế phần từ cuối cùng
          }
        }
        // let indexAddLine = this.trang * 5 - 1
        // this.arrayTem.splice(indexAddLine, 1, DataAddfilterC)// thay thế phần từ cuối cùng
        // this.arrayTem.push(e)
        //   this.Temlate = "";
        //   this.Type = "";
        //   this.Company = "";
        //   this.VersionDate = "";
        //   expirationDate = "";
        //   this.Active = "";
        // this.arrayTemtam = []
        // for (let [, v] of this.arrayTem.entries()) {
        //   this.arrayTemtam.push(v)
        // }
        this.trangtam = this.trang
        this.trang = -10
        // cập nhật rỗng cho các input khi them line mới
        this.idarrayTem = ''
        this.Temlate = ''
        this.Type = ''
        this.Company = ''
        this.VersionDate = ''
        this.expirationDate = ''
        this.Active = ''
      }
    },
    cancelAddLine (e) {
      history.pushState(null, null, 'Home')
      let indexAddLine = this.trang * 5 - 1
      this.arrayTem.splice(indexAddLine, 1)
      // this.arrayTemtam = []
      // for (let [, v] of this.arrayTem.entries()) {
      //   this.arrayTemtam.push(v)
      // }
      this.trangtam = this.trang
      this.trang = -10
    },
    sortData (e) {
      this.checkSearchtam = false
      let tt = e.target.innerHTML.slice(0, 4)
      this.arrayTemtam = []
      for (let i = 0; i <= this.arrayTem.length - 1; i++) {
        this.arrayTemtam.push(this.arrayTem[i])
      }
      history.pushState(null, null, 'sort=' + tt)
      switch (tt) {
        case 'Form':
          this.sortTem = ''
          this.sortTyp = ''
          this.sortCom = ''
          this.sortVer = ''
          this.sortExp = ''
          this.sortACT = ''
          if (this.typeSort === 'up') {
            for (let i = 0; i < this.arrayTem.length - 1; i++) { // buble sort
              for (let j = this.arrayTem.length - 1; j > 0; j--) {
                if (this.arrayTem[j].idfrom < this.arrayTem[ j - 1 ].idfrom) {
                  let tam = {}
                  tam = this.arrayTem[j]
                  this.arrayTem[j] = this.arrayTem[ j - 1 ]
                  this.arrayTem[ j - 1 ] = tam
                }
              }
            }
            this.sortfor = '↓'
            this.typeSort = 'down'
          } else {
            for (let i = 0; i < this.arrayTem.length - 1; i++) { // buble sort
              for (let j = this.arrayTem.length - 1; j > 0; j--) {
                if (this.arrayTem[j].idfrom > this.arrayTem[ j - 1 ].idfrom) {
                  let tam = {}
                  tam = this.arrayTem[j]
                  this.arrayTem[j] = this.arrayTem[ j - 1 ]
                  this.arrayTem[ j - 1 ] = tam
                }
              }
            }
            this.sortfor = '↑'
            this.typeSort = 'up'
          }
          this.trangtam = this.trang
          this.trang = -10
          break
        case 'Type':
          this.sortfor = ''
          this.sortTem = ''
          this.sortCom = ''
          this.sortVer = ''
          this.sortExp = ''
          this.sortACT = ''
          if (this.typeSort === 'up') {
            this.arrayTem.sort((a, b) => {
              let titleA = a.Type.toLowerCase()
              let titleB = b.Type.toLowerCase()
              if (titleA < titleB) return -1
              if (titleA > titleB) return 1
              return 0
            })
            this.sortTyp = '↓'
            this.typeSort = 'down'
          } else {
            this.arrayTem.sort((a, b) => {
              let titleA = a.Type.toLowerCase()
              let titleB = b.Type.toLowerCase()
              if (titleA < titleB) return 1
              if (titleA > titleB) return -1
              return 0
            })
            this.sortTyp = '↑'
            this.typeSort = 'up'
          }
          this.trangtam = this.trang
          this.trang = -10
          break
        case 'TemP':
          this.sortfor = ''
          this.sortTyp = ''
          this.sortCom = ''
          this.sortVer = ''
          this.sortExp = ''
          this.sortACT = ''
          if (this.typeSort === 'up') {
            this.arrayTem.sort((a, b) => {
              let titleA = a.Temlate.toLowerCase()
              let titleB = b.Temlate.toLowerCase()
              if (titleA < titleB) return -1
              if (titleA > titleB) return 1
              return 0
            })
            this.sortTem = '↓'
            this.typeSort = 'down'
          } else {
            this.arrayTem.sort((a, b) => {
              let titleA = a.Temlate.toLowerCase()
              let titleB = b.Temlate.toLowerCase()
              if (titleA < titleB) return 1
              if (titleA > titleB) return -1
              return 0
            })
            this.sortTem = '↑'
            this.typeSort = 'up'
          }
          this.trangtam = this.trang
          this.trang = -10
          break
        case 'Comp':
          this.sortfor = ''
          this.sortTem = ''
          this.sortTyp = ''
          this.sortVer = ''
          this.sortExp = ''
          this.sortACT = ''
          if (this.typeSort === 'up') {
            this.arrayTem.sort((a, b) => {
              let titleA = a.Company.toLowerCase()
              let titleB = b.Company.toLowerCase()
              if (titleA < titleB) return -1
              if (titleA > titleB) return 1
              return 0
            })
            this.sortCom = '↓'
            this.typeSort = 'down'
          } else {
            this.arrayTem.sort((a, b) => {
              let titleA = a.Company.toLowerCase()
              let titleB = b.Company.toLowerCase()
              if (titleA < titleB) return 1
              if (titleA > titleB) return -1
              return 0
            })
            this.sortCom = '↑'
            this.typeSort = 'up'
          }
          this.trangtam = this.trang
          this.trang = -10
          break
        case 'ACTI':
          this.sortfor = ''
          this.sortTem = ''
          this.sortTyp = ''
          this.sortCom = ''
          this.sortVer = ''
          this.sortExp = ''
          if (this.typeSort === 'up') {
            this.arrayTem.sort((a, b) => {
              let titleA = a.Active.toLowerCase()
              let titleB = b.Active.toLowerCase()
              if (titleA < titleB) return -1
              if (titleA > titleB) return 1
              return 0
            })
            this.sortACT = '↓'
            this.typeSort = 'down'
          } else {
            this.arrayTem.sort((a, b) => {
              let titleA = a.Active.toLowerCase()
              let titleB = b.Active.toLowerCase()
              if (titleA < titleB) return 1
              if (titleA > titleB) return -1
              return 0
            })
            this.sortACT = '↑'
            this.typeSort = 'up'
          }
          this.trangtam = this.trang
          this.trang = -10
          break
        case 'Expi':
          this.sortfor = ''
          this.sortTem = ''
          this.sortTyp = ''
          this.sortCom = ''
          this.sortVer = ''
          this.sortACT = ''
          if (this.typeSort === 'up') {
            this.arrayTem.sort((a, b) => {
              a = a.ExpirationDate.toString().split('-')
              b = b.ExpirationDate.toString().split('-')
              return a[2] - b[2] || a[1] - b[1] || a[0] - b[0]
            })
            this.sortExp = '↓'
            this.typeSort = 'down'
          } else {
            this.arrayTem.sort((a, b) => {
              a = a.ExpirationDate.toString().split('-')
              b = b.ExpirationDate.toString().split('-')
              return b[2] - a[2] || b[1] - a[1] || b[0] - a[0]
            })
            this.sortExp = '↑'
            this.typeSort = 'up'
          }
          this.trangtam = this.trang
          this.trang = -10
          break
        case 'Vers':
          this.sortfor = ''
          this.sortTem = ''
          this.sortTyp = ''
          this.sortCom = ''
          this.sortVer = ''
          this.sortACT = ''
          if (this.typeSort === 'up') {
            this.arrayTem.sort((a, b) => {
              a = a.VersionDate.toString().split('-')
              b = b.VersionDate.toString().split('-')
              return a[2] - b[2] || a[1] - b[1] || a[0] - b[0]
            })
            this.sortVer = '↓'
            this.typeSort = 'down'
          } else {
            this.arrayTem.sort((a, b) => {
              a = a.VersionDate.toString().split('-')
              b = b.VersionDate.toString().split('-')
              return b[2] - a[2] || b[1] - a[1] || b[0] - a[0]
            })
            this.sortVer = '↑'
            this.typeSort = 'up'
          }
          this.trangtam = this.trang
          this.trang = -10
          break
      }
    },
    removeline (e) {
      this.evenremove = e
      this.arrayTemtam = []
      // for (let i = 0; i <= this.arrayTem.length - 1; i++) {
      //   this.arrayTemtam.push(this.arrayTem[i])
      // }
      this.trangtam = this.trang
      this.trang = -10
    },
    filterData (e) {
      history.pushState(null, null, 'filter')
      this.showFilter = true
    },
    confirmFilter (e) {
      // if (this.search.length !== 0) {
      this.checkSearchtam = true
      // }
      // this.searchtam = []
      // for (let [i] of this.arrayTem.entries()) {
      //   this.searchtam.push(this.arrayTem[i])
      // }
      // for (let i = this.searchtam.length - 1; i >= 0; i--) {
      //   if (this.searchtam[i].Temlate.includes(this.search)) {
      //   } else {
      //     this.searchtam.splice(i, 1)
      //   }
      // }
      this.showFilter = false
      this.searchtam = []
      for (let i = 0; i <= this.arrayTem.length - 1; i++) {
        this.searchtam.push(this.arrayTem[i])
      }
      if (e.checkall === 'loc') {
        for (let i = this.searchtam.length - 1; i >= 0; i--) {
          if (this.searchtam[i].Type.includes(e.Type)) {
          } else {
            this.searchtam.splice(i, 1)
          }
        }
        for (let i = this.searchtam.length - 1; i >= 0; i--) {
          if (this.searchtam[i].Company.includes(e.Company)) {
          } else {
            this.searchtam.splice(i, 1)
          }
        }
        for (let i = this.searchtam.length - 1; i >= 0; i--) {
          if (this.searchtam[i].Active.includes(e.Active)) {
          } else {
            this.searchtam.splice(i, 1)
          }
        }

        //  if (e.VersionDate !== '' && e.VersionDate[4] === '-') { e.VersionDate = this.convertDate(e.VersionDate, '-', 'yyyy_mm_dd') }
        if (e.VersionDate1[4] === '-') {
          for (let i = this.searchtam.length - 1; i >= 0; i--) {
            let numberVer
            let ngayv = Number(this.searchtam[i].VersionDate.slice(0, 2))
            let thangv = Number(this.searchtam[i].VersionDate.slice(3, 5))
            let namv = Number(this.searchtam[i].VersionDate.slice(6, 10))
            numberVer = namv * 360 + thangv * 30 + ngayv
            let ngay
            let thang
            let nam
            let dayNumber1
            let datNumber2
            if (e.VersionDate1.slice(4, 5) === '-') {
              ngay = Number(e.VersionDate1.slice(0, 4))
              thang = Number(e.VersionDate1.slice(5, 7))
              nam = Number(e.VersionDate1.slice(8, 10))
              dayNumber1 = ngay * 360 + thang * 30 + nam
            }
            if (e.VersionDate2.slice(4, 5) === '-') {
              ngay = Number(e.VersionDate2.slice(0, 4))
              thang = Number(e.VersionDate2.slice(5, 7))
              nam = Number(e.VersionDate2.slice(8, 10))
              datNumber2 = ngay * 360 + thang * 30 + nam
            }
            if (dayNumber1 <= numberVer && numberVer <= datNumber2) {
            } else {
              this.searchtam.splice(i, 1)
            }
          }
        }
      } else {
      }
      this.checkFilterData = ''
      this.trangtam = this.trang
      this.trang = -10
    },
    closeFilter (e) {
      this.showFilter = false
    },
    allData (e) {
      this.checkSearchtam = false
      this.showFilter = false
      this.arrayTemtam = []
      for (let [, v] of this.arrayTem.entries()) {
        this.arrayTemtam.push(v)
      }
      this.trangtam = this.trang
      this.trang = -10
    },
    dropLeft (e) { // kiểm tra dropup hiển thị và ẩn
      let checkEvent
      try {
        checkEvent = e.target.getAttribute('check') // nếu lỗi thì e là một đối tượng được gọi hàm trong methods
        checkEvent = e.target
      } catch (err) {
        checkEvent = e
      }
      if (checkEvent.getAttribute('check') === '0') {
        checkEvent.parentNode.style = 'display: block'
        checkEvent.parentNode.childNodes[2].style = 'display: block'
        checkEvent.setAttribute('check', '1')
      } else {
        checkEvent.parentNode.style = 'display: inline-block'
        checkEvent.parentNode.childNodes[2].style = 'display: none'
        checkEvent.setAttribute('check', '0')
      }
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
    // randomNumber: function () {
    randomNumber: function () {
      let random10019999 = 1
      let t = true
      while (t) {
        random10019999 = parseInt(Math.random() * (9999 - 1001) + 1001)
        let i = 0
        for (i = 0; i < this.arrayTem.length; i++) {
          if (String(random10019999) === this.arrayTem[i].idfrom) {
            break
          }
        }
        if (i < this.arrayTem.length - 1) t = true
        else t = false
      }
      return random10019999
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

}
#hahaserch {
  width: 600px;
  height: 30px;
  border: 2px solid blue;
  border-radius: 5px;

}
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
  z-index: 5;
  min-width: 1100px;
  padding: 0px;
  margin: 0px;
  color: red;
  display: flex;
  background-color: rgb(255, 0, 0);
  border-top-right-radius: 10px;
  border-top-left-radius: 10px;
}
.flex-container > .style {
  background-color: rgb(255, 0, 0);
  font-size: 20px;
  padding: 10px;
  flex:1;
  border: 1px solid black;
  color: white;
}
.flex-container > .style:hover {
    background-color: rgb(247, 173, 173);
    cursor: ns-resize;
    color: black
}
.flex-container > div {
  background-color: rgb(255, 255, 255);
  color: rgb(0, 0, 0);
  border: 1px solid black;
  padding: 10px;
  font-size: 10px;
  flex:1;
}
.flex-container:first-child div:last-child {
  background-attachment: fixed;
  background-color: D0CFCF;
}
#container {
   flex: 1;
   display: flex;
   flex-direction: column;
}
#bang {
  flex: 1;
  position: relative;
  border-top-left-radius: 15px;
  border-top-right-radius: 15px;
  display: flex;
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
  display: flex;
  position: absolute;
  width: 100%;
  text-align: center;
  bottom: 25px;
  background-color: none;
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
.dropbtn {
  font-size: 20px;
  height: 5px;
  background-color: #ffffff;
  border: 0px;
  outline:#ffffff
}

.dropup {
  position: relative;
  display: inline-block;
}

.dropup-content {
  border: 1px solid blue;
  display: none;
  position: absolute;
  background-color: #ffffff;
  min-width: 60px;
  bottom: -20px;
  right: 85px;
  z-index: 1;
}

.dropup-content>button {
 background-color: #ffffff;
  color: black;
  padding: 4px;
  border: none;
  outline: none;
  text-decoration: none;
  width: 100%;
  display: inline-block;
}

.dropup-content>button:hover {background-color: rgb(204, 204, 204)}

/* .dropup:hover .dropup-content {
  display: block;
} */

</style>
