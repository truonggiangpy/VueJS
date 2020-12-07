<template>

  <div id="app">
   
    <containers v-bind:form="form" v-on:changeeven="changeevenn"></containers>
     <modal v-bind:create_confirm_boolean="create_confirm_boolean" v-on:CreteForm="CreteForm"></modal>
  </div>
</template>
<script>

import containers from './components/containers.vue';
import modal from './components/modal.vue';
export default {
  name: 'App',
  data () {
    return {
      title: 'giang',
      create_confirm_boolean: 'd',
      // form: {},

      form: [
        // Temlate: this.Temlate,Type: this.Type, Company: this.Company,VersionDate: this.VersionDate, ExpirationDate: this.ExpirationDate, Active: this.Active
          {idfrom:'1111',Temlate: 'giang', Type:'Production',Company: "Peptico",VersionDate: '20-11-2020',ExpirationDate: '20-11-2020', Active: 'Active'},
          {idfrom:'1111',Temlate: 'giang', Type:'Production',Company: "Peptico",VersionDate: '20-11-2020',ExpirationDate: '20-11-2020', Active: 'Active'},
          {idfrom:'1111',Temlate: 'giang', Type:'Production',Company: "Peptico",VersionDate: '20-11-2020',ExpirationDate: '20-11-2020', Active: 'Active'},
          {idfrom:'1111',Temlate: 'giang', Type:'Production',Company: "Peptico",VersionDate: '20-11-2020',ExpirationDate: '20-11-2020', Active: 'Active'},
          {idfrom:'1111',Temlate: 'giang', Type:'Production',Company: "Peptico",VersionDate: '20-11-2020',ExpirationDate: '20-11-2020', Active: 'Active'},
      ]
    }
  },
  components: {
    containers,
    modal
  },
      methods: {
        convertDate: function(Datee){
        var ngay
        var thang
        var nam
 
        if(Datee[4]=='-'){
        nam=Datee.slice(0,4)
        thang=Datee.slice(5,7)
        ngay=Datee.slice(8,10)
          return ngay+'-'+ thang +'-'+ nam
       }

        },
        random_number: function(){
          var random_1001_9999 = 1;
          var t= true;
          while(t){
          random_1001_9999 = parseInt(Math.random() * (9999 - 1001) + 1001);
          var i=0;
          for(i=0; i < this.form.length; i++){
              if(String(random_1001_9999) == this.form[i].idfrom){
                  break;
              }
          }
          if(i<this.form.length-1)
              t=true;
          else
              t=false;
          }
          return random_1001_9999;
        },
        
        CreteForm(e){
          e.ExpirationDate=this.convertDate(e.ExpirationDate)
          e.VersionDate=this.convertDate(e.VersionDate)
  
       e.idfrom =this.random_number()

         this.form.push(e) // cập nhật lại giá trị form
        },
        
    changeevenn(e) {
     this.create_confirm_boolean=e.chuoi;
     //console.log("apphihi"+ this.create_confirm_boolean)
      // this.$emit('changeeven',e)
    }
  }
}

</script>

<style>
#app{
  margin: 0px;
  padding:0px;
  position: relative;
}
body {
  margin: 0px;
  padding:0px;
  position: relative;
}
</style>
