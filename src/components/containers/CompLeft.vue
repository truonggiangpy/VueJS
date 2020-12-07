<template>
  <div id="container_left">
    <div id="content">
      <div id="logo">
        <div style="color: white; font-size: 45px;">MAZI</div>
        <div style="padding-bottom: 7px ">&nbsp; v1.00</div>
      </div>
      <hr />
      <div><a href="javascript:;">Dashboard</a></div>
      <div><a href="javascript:;">Project</a></div>
      <div class="marinleft"><a href="javascript:;">Campaigns</a></div>
      <div class="marinleft"><a href="javascript:;">Jobs</a></div>
      <hr />
      <div><a href="javascript:;">Assets</a></div>
      <div><a href="javascript:;">Elements</a></div>
      <div><a href="javascript:;">Research</a></div>
      <div><a href="javascript:;">People</a></div>
      <div><a href="javascript:;">Companies</a></div>
      <hr />
      <div><a href="javascript:;">Contract</a></div>
      <div class="marinleft"><a href="javascript:;">All Contracts</a></div>
      <div class="marinleft"><a href="javascript:;">Contract Templates</a></div>
      <div class="marinleft"><a href="javascript:;">Snippets</a></div>
      <hr />
      <div><a href="javascript:;">Forms</a></div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Contaiv',
  data () {
    return {
      msg: ''
    }
  }
}

</script>
<style scoped>
.marinleft {
  margin-left: 10px;
}
#content {
  margin: 20px;
  color: white;
}

#container_left {
  background-color: #101e33;
  width: 200px;
  height: 100vh;
}

#container_left > div {
  padding: 20px;
}

#content > div {
  padding: 5px;
}

#logo {
  display: flex;
  align-items: flex-end;
}

a {
  text-decoration: none;
  color: white;
}
</style>
