<template>
  <div id="app">
    <PipelineTable></PipelineTable>
  </div>
</template>

<script>
import PipelineTable from "@/components/Table";

export default {
  name: 'App',
  components: {
    PipelineTable
  },
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
