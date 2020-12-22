<template>
  <div id="right">
    <CompTop/>
    <CompContent/>
  </div>
</template>
<script>
import CompTop from './compRight/compTop'
import CompContent from './compRight/compContent'
export default {
  name: 'right',
  components: {
    CompTop,
    CompContent
  }
}

</script>
<style scoped>
#right {
  display: flex;
     flex-direction: column;
    flex: 1;
    margin:0px 5px;

  overflow-y: overlay;
}
</style>
