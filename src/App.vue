<template>
<body>
  <div id="app">
<!-- //lọc dữ liệu sắp xếp tìm kiếm -->
    <!-- <div>{{Loc}}</div> -->
    <compLeft/>
    <compRight/>
    <!-- <CompFilter/> -->
  </div>
</body>
</template>
<script>
import compLeft from './components/compLeft'
import compRight from './components/compRight'
export default {
  name: 'App',
  components: {
    compLeft,
    compRight
  }
}
</script>
<style>
#app {
  margin: 0px;
  padding: 0px;
  position: relative;
  display: flex;
}
body {
  margin: 0px;
  padding: 0px;
  position: relative;
}
</style>
