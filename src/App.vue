<script setup>
import HelloWorld from './components/HelloWorld.vue'
</script>

<template>
  
<div>  
  <h1>学生管理系统</h1>

<!-- 学生信息输入表单 -->
<h2>添加学生</h2>
<form @submit.prevent="addStudent">
  <label for="name">姓名: </label>
  <input v-model="newStudent.name" type="text" id="name" placeholder="请输入学生姓名" required>
  <label for="age">年龄: </label>
  <input v-model="newStudent.age" type="number" id="age" placeholder="请输入学生年龄" required>
  <label for="course">课程: </label>
  <input v-model="newStudent.course" type="text" id="course" placeholder="请输入学生课程" required>
  <button type="submit" class="button">添加学生</button>
</form>

<!-- 查询功能 -->
<div class="search-container">
  <label for="search">查询学生: </label>
  <input v-model="searchQuery" type="text" id="search" placeholder="输入姓名查询">
</div>

<!-- 学生列表 -->
<h2>学生列表</h2>
<table id="studentsTable">
  <thead>
    <tr>
      <th>姓名</th>
      <th>年龄</th>
      <th>课程</th>
      <th>操作</th>
    </tr>
  </thead>
  <tbody>
    <!-- 学生数据将被插入到这里 -->
    <tr v-for="(student, index) in filteredStudents" :key="index">
          <td>{{ student.name }}</td>
          <td>{{ student.age }}</td>
          <td>{{ student.course }}</td>
          <td><button class="button delete-button" @click="deleteStudent(index)">删除</button></td>
        </tr>
  </tbody>
</table>

<!--提交学生信息-->
<div><input type="submit" class="submit" value="提交信息" @click="submitAllStudents"></div>
</div>
</template>

<style scoped>
body {
  font-family: Arial, sans-serif;
  margin: 20px;
  font-size: 18px;
  background: url(images/timg.jpg) no-repeat top center;
}

table {
  width: 100%;
  border-collapse: collapse; /*合并边框*/
  margin-top: 20px;
}

table, th, td {
  border: 1px solid black;
}

th, td {
  padding: 10px;
  text-align: left;
}

.button {
  padding: 8px 16px;
  background-color: #6ed872;
  color: white;
  border: none;
  cursor: pointer;
}

.button:hover {
  background-color: #6ed872;
  opacity: 0.7;
}

.delete-button {
  background-color: #f44336;
}

.delete-button:hover {
  background-color: #e53935;
  opacity: 0.7;
}

.search-container {
  margin: 20px 0;
}

#name, #age, #course, #search {
  border-radius: 5px;
  opacity: 0.7;
  background: 5px center rgba(255, 255, 255, 0.5);
}

h1 {
  text-align: center;
  margin-top: 50px;
  color: white;
  opacity: 0.8;
}

h2 {
  color: white;
  opacity: 0.7;
}

#studentsTable {
  background-color: rgb(255, 255, 255);
  opacity: 0.7;
}

.submit {
  width: 100px;
  height: 35px;
  margin: 35px 47%;
  border: 1px solid #000;
}

.submit:hover {
  background-color: rgb(167, 158, 158);
}
</style>
