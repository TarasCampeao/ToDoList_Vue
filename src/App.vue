<style lang="sass">
    @import url('https://use.fontawesome.com/releases/v5.3.1/css/all.css')
    @import "./assets/style/main.sass"
    @import "./assets/style/media.sass"
</style>
<template>
  <div id="app">
    <div class="container">
      <task-list></task-list>
    </div>
  </div>
</template>

<script>
import TaskList from './components/TaskList.vue'


export default {
  name: 'app',
  components: {
    TaskList,
  },
};
</script>


