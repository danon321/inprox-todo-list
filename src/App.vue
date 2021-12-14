<template>
  <div id="app">
    <div class="container">
      <Header :title="'Tasker'" :subtitle="'Task menager for everyone'" />
      <Blob :position="'top'" />
      <TodoList />
    </div>
    <Blob :position="'right'" />
    <Blob :position="'left'" />
  </div>
</template>

<script>
import Header from '@/components/Header.vue';
import TodoList from '@/components/TodoList.vue';
import Blob from '@/components/Blob.vue';

export default {
  name: 'App',
  components: {
    Header,
    TodoList,
    Blob
  }
}
</script>

<style lang="scss" scoped>
  @import "@/styles/layout/_app.scss";
</style>