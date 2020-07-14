<template>
  <div id="app">
    <div 
    v-for="node in tree" 
    v-bind:key="node.id">
    <TreeBrowser
      :node="node"
     />
     </div>
  </div>
</template>

<script>
import TreeBrowser from './components/TreeBrowser.vue'
import treeData from './resources/tree.json'

export default {
  name: 'App',
  data() {
    return {
        tree: treeData
    }
  },
  components: {
    TreeBrowser
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
