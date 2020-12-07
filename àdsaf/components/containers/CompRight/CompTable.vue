<template>
  <div id="bang">
    <div class="flex-container">
      <div class="style col1" style="border-top-left-radius: 10px;">
        Form ID#
      </div>
      
      <div class="style col2">TemPlate Name</div>
      <div class="style col3">Type</div>
      <div class="style col4">Company</div>
      <div class="style col5">Version Date</div>
      <div class="style col6">Expiration D</div>
      <div class="style col7">ACTIVE</div>
      <div class="style col8" style="border-top-right-radius: 10px;"></div>
    </div>
    <div id="tablefull">
      <div class="tdata">
        <!-- <div class="flex-container">
          <div class="col1">1111</div>
          <div class="col2">1337-AFM-B6-TV-RADIOCOMMERCIALS-11-15-19</div>
          <div class="col3">Production</div>
          <div class="col4">PEPCICO</div>
          <div class="col5">20-11-2020</div>
          <div class="col6">20-11-2020</div>
          <div class="col7">Archive</div>
          <div class="col8" style="text-align: center;">
            <a href="#" class="add">Edit</a>
            <a href="#id01" class="remove">Remove</a>
          </div>
        </div> -->
        


        <div class="flex-container" v-for="user in form" :key="user" >
          <div class="col1">{{user.idfrom}}</div>
          <div class="col2">{{user.Temlate}}</div>
          <div class="col3">{{user.Type}}</div>
          <div class="col4">{{user.Company}}</div>
          <div class="col5">{{user.VersionDate}}</div>
          <div class="col6">{{user.ExpirationDate}}</div>
          <div class="col7">{{user.Active}}</div>
          <div class="col8" style="text-align: center;">
            <a href="#" class="add">Edit</a>
            <a href="#id01" class="remove">Remove 


            </a>
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
      <button v-if="form.Temlate">dsa</button>
    
  </div>
  
</template>
<script>
export default {
  name: "bang",
    props: {
      
    form: Array,
 
  },

  data() {
    return {
      msg: "",

      // users: [
      //   // Temlate: this.Temlate,Type: this.Type, Company: this.Company,VersionDate: this.VersionDate, ExpirationDate: this.ExpirationDate, Active: this.Active
      //     {Temlate: 'giang', Type:'Production',Company: "Peptico",VersionDate: '20-11-2020',ExpirationDate: '20-11-2020', Active: 'Active'},
      //     {Temlate: 'giang', Type:'Production',Company: "Peptico",VersionDate: '20-11-2020',ExpirationDate: '20-11-2020', Active: 'Active'},
      //     {Temlate: 'giang', Type:'Production',Company: "Peptico",VersionDate: '20-11-2020',ExpirationDate: '20-11-2020', Active: 'Active'},
      //     {Temlate: 'giang', Type:'Production',Company: "Peptico",VersionDate: '20-11-2020',ExpirationDate: '20-11-2020', Active: 'Active'},
      //     {Temlate: 'giang', Type:'Production',Company: "Peptico",VersionDate: '20-11-2020',ExpirationDate: '20-11-2020', Active: 'Active'},
      // ]
    }
  },

  computed: {

  },
  methods: {
    giang: function(){

       this.users.push(this.form)
    }
  },

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
