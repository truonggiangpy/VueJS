<template>
  <div id="id01" class="modal">
    <div class="modal-dialog">
      <div class="modal-content">
        <header class="container">
          <div class="container">
            <div class="row">
              <div class="col-75">
                <label>Temlate Name </label><input class="create" value="" v-model="Temlate" placeholder="Nhập Temlate">
              </div>
            </div>
            <div class="col-75">
              <label>Type</label>
              <select class="create"  v-model="Type">
                <option disabled value="">Chọn Type</option>
                <option>Payoll</option>
                <option>Production</option>
              </select>

            </div>
            <div class="col-75">
              <label>Company</label>
              <input class="create" v-model="Company" placeholder="Nhập Company">
              
            </div>
            <label>Version Date</label>  <input class="create" type="date" v-model="VersionDate"/>
            <label>Expiration D</label> <input class="create"  type="date" v-model="ExpirationDate"/>
            <div class="col-75">
              <label>Active</label>
              <select class="create"  v-model="Active">
                <option disabled value="">Chọn </option>
                <option>Active</option>
                <option>Archive</option>
              </select>
            </div>
          </div>
        </header>
        <footer class="container1">
          <template v-if="create_confirm_boolean === 'Create'">
               <a href="#" v-on:click="Click_Form" class="closebtn" id="cancel">Create</a> &nbsp; &nbsp;
           
          </template>
          <template v-else>
            <a href="#" class="closebtn" id="cancel">Confirm</a> &nbsp; &nbsp;
           
          </template>
          <a href="#" class="closebtn" id="cancel">cancel</a> &nbsp; &nbsp;
      
        </footer>
  

      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "ds",
    props: {
    create_confirm_boolean: String,
  },
  data() {
    return {
      Temlate: "",
      Type: '',
      Company: '',
      VersionDate: '',
      ExpirationDate: '',
      Active: '',
      loginType: 'Confirm',
      msg: ""
    };
  },
  methods: {
      Click_Form(e) {
          var form={idfrom:"",Temlate: this.Temlate,Type: this.Type, Company: this.Company,VersionDate: this.VersionDate, ExpirationDate: this.ExpirationDate, Active: this.Active}
          this.$emit('CreteForm',form)
          this.Temlate=''
          this.Type=''
          this.Company=''
          this.VersionDate=''
          this.ExpirationDate=''
          this.Active=''
      }
  }
};

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
  display: none;
  position: fixed;
  left: 0;
  top: 0;
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
  display: table-cell;
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
 
}
.create {
  margin-top: 10px;
}
</style>
