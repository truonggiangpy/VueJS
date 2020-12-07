<template>
    <div id="container_child">
        <div id="title">
            <div ><a href="javascript:;" style="color: blue"> Dashboard &rsaquo; Contract Templates</a></div>
            <div >
                <form class="example" action="" style="margin:auto; max-width:300px; display: flex; " >
                    <input size="25" style="border-radius: 7px; outline: none  " type="text" placeholder="Search.." >
                    <button style="width: 100px; "  type="submit" >Tìm Kiếm</button>  
                </form>
            </div>
            <div  >
                <form class="example" action="" style="margin:auto; max-width:300px; " >
                    <button href="javascript:;" class="tron" >^^</button>  
                    <button href="javascript:;" class="tron">*</button>  
                    <button href="javascript:;" class="tron">0</button>  
                </form>
            </div>
        </div>
            <hr>
        <h1 id="container1">Contract Templates</h1>

        <div class="container2">
            <div style="color:blue">Union(8) &nbsp;  &nbsp;   </div>
            <div>Non-Union(12)  &nbsp; </div>
            <div>MSA(3)</div>
        </div>
        <hr>
        <div class="container2">
            
            <div style="color:blue" ><a v-on:click="Handlechange" href="#id01" id="Union"  style="color: blue;">+ Union Templates &nbsp;  &nbsp;</a>   </div>
            <div style="color:blue" ><a href="#" id="Filter"  style="color: blue;">Add Filter &nbsp;  &nbsp;</a>   </div>
            <!-- <div>Add Filter  &nbsp; </div> -->
            <div>OSearch</div>
             
        </div>
     
        </div>
        
</template>

<script>

export default {
  name: "Control",

  props: {
    form: Object,
   
  },
  data () {
    return {
      msg: ""
    };
  },
  methods: {
      Handlechange(e, ) {
          var data={chuoi: 'Create'}
          this.$emit('changeeven',data)
        
      }
  }

};

</script>
<style scoped>
#container_child{
    display: flex;
    flex-direction: column;
    padding-bottom: 0;
    }
#container_right{
    height: 100vh;
	background: #a5acb1;
	padding:0px 10px;
    flex:1;
    display: flex;
    flex-direction: column;
}
#title{
	display: flex;
	justify-content: space-between;
	align-items: center;
	height: 40px;
}

.container {
  padding: 2px 16px;
}

.container2{
	display: flex;
}


.container1 {
    padding: 2px 16px;
    display: flex;
    justify-content: flex-end;
  }
    a{
      text-decoration: none;
      color: white;
  }
</style>