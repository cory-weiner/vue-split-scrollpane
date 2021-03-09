<template>
  <div>
    <SplitPane>
      <LoremIpsum/>
    </SplitPane>
  </div>
</template>

<script>
import SplitPane from './components/SplitPane.vue'
import LoremIpsum from './components/LoremIpsum.vue'
export default {
  name: 'App',
  components: {
    SplitPane,
    LoremIpsum
  }
}
</script>

<style>
body{
  padding:0px;
  margin: 0px;
}
</style>
