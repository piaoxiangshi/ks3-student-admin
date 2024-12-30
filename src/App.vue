<template>
  <div id="app">
    <StudentSearch />
  </div>
</template>

<script>
// 导入 StudentSearch 组件
import StudentSearch from './layout/components/StudentSearch.vue';

export default {
  name: 'App',
  components: {
    StudentSearch // 注册组件
  }
};
</script>

<style>
/* 样式可以自定义 */
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  color: #2c3e50;
  margin-top: 50px;
}
</style>
