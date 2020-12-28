<template>
  <div class="modal">
    <div class="modal-dialog">
      <template v-if="confirmBoolean === 'Create'">
        <div class="modal-content">
          <header class="container">
            <div class="container">
              <div class="row">
                <div class="col-75">
                  <label>Temlate Name </label
                  ><input
                    class="create"
                    v-model.trim="msg"
                    v-model="Temlate"
                    placeholder="Nhập Temlate"
                  />
                </div>
              </div>

              <div class="col-75">
                <label>Temlate</label>
                <select class="create" v-model="Type">
                  <option disabled value="">Chọn Type</option>
                  <option>Payoll</option>
                  <option>Production</option>
                </select>
              </div>
              <div class="col-75">
                <label>Company</label>
                <input
                  class="create"
                  v-model="Company"
                  placeholder="Nhập Company"
                />
              </div>
              <label>Version Date</label>
              <input class="create" type="date" v-model="VersionDate" />
              <label>Expiration D</label>
              <input class="create" type="date" v-model="ExpirationDate" />
              <div class="col-75">
                <label>Active</label>
                <select class="create" v-model="Active">
                  <option disabled value="">Chọn </option>
                  <option>Active</option>
                  <option>Archive</option>
                </select>
              </div>
            </div>

            <label style=" color: red">{{mess}}</label>
          </header>
          <footer class="container1">
            <a href="#" v-on:click="createTem" class="closebtn" id="cancel"
              >Create</a
            >
            &nbsp; &nbsp;
            <a href="#" v-on:click="cancelCreteTem" class="closebtn" id="cancel"
              >cancel</a
            >
            &nbsp; &nbsp;

          </footer>

        </div>
      </template>
      <template v-else>
        <div class="modal-content">
          <header
            class="container"
            style="text-align:center; font-size:20px; color: white"
          >
            <div class="container">
              <h1>Xác Nhận Xóa</h1>
              <div><label>FormID: </label>{{ evenRemove.id }}</div>
              <div><label>Temlate: </label>{{ evenRemove.Temlate }}</div>
              <div><label>Type: </label>{{ evenRemove.Type }}</div>
              <div><label>Company: </label>{{ evenRemove.Company }}</div>
              <div>
                <label>VersionDate: </label>{{ evenRemove.VersionDate }}
              </div>
              <div>
                <label>ExpirationDate: </label>{{ evenRemove.ExpirationDate }}
              </div>
              <div><label>Active: </label>{{ evenRemove.Active }}</div>
            </div>
          </header>
          <footer class="container1">
            <template v-if="confirmBoolean === 'Create'">
              <a href="#" v-on:click="Click_Form" class="closebtn" id="cancel"
                >Create</a
              >
              &nbsp; &nbsp;
            </template>
            <template v-else>
              <a href="#" class="closebtn" id="cancel" v-on:click="confirmRemove"
                >Confirm</a
              >
              &nbsp; &nbsp;
            </template>
            <a href="#" class="closebtn" id="cancel" v-on:click="cancelRemove">cancel</a> &nbsp; &nbsp;
          </footer>
        </div>
      </template>
    </div>
    <div class="modal2" v-show="confirmCan">
    <div class="modal-dialog">
      <template>
        <div class="modal-content">
          <header
            class="container"
            style="text-align:center; font-size:20px; color: white"
          >
            <div class="container">
              <h1>Xác Nhận Cancel</h1>
              <div><label>Temlate: </label>{{ confirmCamcell.Temlate }}</div>
              <div><label>Type: </label>{{ confirmCamcell.Type }}</div>
              <div><label>Company: </label>{{ confirmCamcell.Company }}</div>
              <div>
                <label>VersionDate: </label>{{ confirmCamcell.VersionDate }}
              </div>
              <div>
                <label>ExpirationDate: </label>{{ confirmCamcell.ExpirationDate }}
              </div>
              <div><label>Active: </label>{{ confirmCamcell.Active }}</div>
            </div>
          </header>
          <footer class="container1">
            <template v-if="confirmBoolean === 'Create'">
              <a href="#" class="closebtn" id="cancel" v-on:click="confirmCancel"
                >Confirm</a
              >
              &nbsp; &nbsp;
            </template>
            <template v-else>
              <a href="#" class="closebtn" id="cancel"
                >Confirm</a
              >
              &nbsp; &nbsp;
            </template>
            <a href="#" class="closebtn" id="cancel" v-on:click="cancelCancel">cancel</a> &nbsp; &nbsp;
          </footer>
        </div>
      </template>
    </div>
  </div>
  </div>

</template>

<script>
// alert(e.id+e.Temlate+e.Type+e.Company+e.VersionDate+e.ExpirationDate+e.Active)
export default {
  name: 'ds',
  props: {
    confirmBoolean: String,
    evenRemove: Object
  },
  data () {
    return {
      confirmCan: false,
      confirmCamcell: {Temlate: '', Type: '', Company: '', VersionDate: '', ExpirationDate: '', Active: ''},
      mess: '',
      Temlate: '',
      Type: '',
      Company: '',
      VersionDate: '',
      ExpirationDate: '',
      Active: '',
      loginType: '',
      msg: ''
    }
  },
  computed: {
  },
  methods: {
    createTem (e) {
      if (this.Temlate === '') {
        this.mess = 'Trường Template chưa được nhập'
      } else {
        this.mess = ''
        var form = {
          idfrom: '',
          Temlate: this.Temlate,
          Type: this.Type,
          Company: this.Company,
          VersionDate: this.VersionDate,
          ExpirationDate: this.ExpirationDate,
          Active: this.Active,
          node1: 'Remove',
          node2: 'Edit',
          return_confirmBoolean: ''
        }

        this.$emit('createTem', form)
        this.Temlate = ''
        this.Type = ''
        this.Company = ''
        this.VersionDate = ''
        this.ExpirationDate = ''
        this.Active = ''
      }
    },
    cancelCreteTem (e) {
      // alert(this.ExpirationDate + this.Type)
      // if (this.Temlate === '' && this.Type === '' && this.Company === '' && this.VersionDate === '' && this.ExpirationDate === '' && this.Active === '') {
      if (this.Temlate === '' && this.Type === '' && this.Company === '' && this.VersionDate === '' && this.ExpirationDate === '' && this.Active === '') {
        this.$emit('confirmCancel', true)
        this.mess = ''
      } else {
        this.confirmCan = true
        this.confirmCamcell.Temlate = this.Temlate
        this.confirmCamcell.Type = this.Type
        this.confirmCamcell.Company = this.Company
        this.confirmCamcell.VersionDate = this.convertDate(this.VersionDate.trim(), '-', 'yyyy_mm_dd')
        this.confirmCamcell.ExpirationDate = this.convertDate(this.ExpirationDate.trim(), '-', 'yyyy_mm_dd')
        this.confirmCamcell.Active = this.Active
      }
    },
    confirmCancel (e) {
      this.mess = ''
      this.confirmCan = false
      this.$emit('confirmCancel', true)
    },
    cancelCancel (e) {
      this.confirmCan = false
    },
    confirmRemove (e) {
      let data1 = { id: this.evenRemove.id }
      this.$emit('confirmRemove', data1)
    },
    cancelRemove (e) {
      let t = false
      this.$emit('cancelRemove', t)
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
    }
  }
}
</script>

<style scoped>
.dialog {
  position: fixed;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
  z-index: 10;
  display: flex;
  align-items: center;
  justify-content: center;
  visibility: hidden;
  opacity: 0;
}
.overlay {
  background-color: 1px solid red;
}

.dielog:target {
  visibility: visible;
  opacity: 1;
}

.dialog-body {
  max-width: 400px;
  position: relative;
  padding: 15px;
  background-color: #d0cfcf;
}

@-webkit-keyframes example {
  from {
    top: -100px;
    opacity: 0;
  }
  to {
    top: 0px;
    opacity: 1;
  }
}

/* Add animation (Standard syntax) */
@keyframes example {
  from {
    top: -100px;
    opacity: 0;
  }
  to {
    top: 0px;
    opacity: 1;
  }
}

/* The modal's background */
.modal {
  z-index: 15;
  position: fixed;
  left: 0;
  top: 0%;
  width: 100%;
  height: 100%;
  overflow: auto;
  background-color: rgb(0, 0, 0);
  background-color: rgba(0, 0, 0, 0.4);
}

/* Display the modal when targeted */
.modal:target {
  display: table;
  position: absolute;
}

/* The modal box */
.modal-dialog {
  vertical-align: middle;
}

/* The modal's content */
.modal-dialog .modal-content {
  margin: auto;
  background-color: #f3f3f3;
  position: relative;
  padding: 0;
  outline: 0;
  border: 1px #777 solid;
  text-align: justify;
  width: 40%;
  box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2), 0 6px 20px 0 rgba(0, 0, 0, 0.19);

  /* Add animation */
  -webkit-animation-name: example; /* Chrome, Safari, Opera */
  -webkit-animation-duration: 0.5s; /* Chrome, Safari, Opera */
  animation-name: example;
  animation-duration: 0.5s;
}

.container1 {
  padding: 2px 16px;
  display: flex;
  justify-content: center;
  background-color: #a5acb1;
}
.closebtn {
  text-decoration: none;
  float: right;
  font-size: 35px;
  background-color: red;
  font-weight: bold;
  border: red 1px solid;
  color: #fff;
}
.container {
  padding: 10px 16px;
  background-color: #a5acb1;
}
.container1 {
  padding: 2px 16px;
  display: flex;
      justify-content: center;
}
.create {
  margin-top: 10px;
}
</style>
