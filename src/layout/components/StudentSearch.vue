<template>
    <div>
      <h1>学生查询</h1>
  
      <!-- 查询表单 -->
      <form @submit.prevent="searchStudents">
        <label for="name">学生姓名：</label>
        <input type="text" v-model="name" placeholder="请输入学生姓名" required>
        <button type="submit" class="button">查询学生</button>
      </form>
  
      <!-- 查询结果 -->
      <table v-if="students.length > 0">
        <thead>
          <tr>
            <th>姓名</th>
            <th>年龄</th>
            <th>班级</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="(student, index) in students" :key="index">
            <td>{{ student.name }}</td>
            <td>{{ student.age }}</td>
            <td>{{ student.className }}</td>
          </tr>
        </tbody>
      </table>
  
      <!-- 如果没有结果 -->
      <p v-else>没有找到相关学生</p>
    </div>
  </template>
  
  <script setup>
  import { ref } from 'vue';

  // 定义响应式数据
  const name=ref('');
  const allStudents=ref([
  { name: '张三', age: 18, className: '一班' },
  { name: '李四', age: 17, className: '二班' },
  { name: '王五', age: 19, className: '三班' }
  ]);


  // 存储过滤后的学生数据
  const students = ref(allStudents.value);

  
// 查询学生函数
function searchStudents() {
  if (name.value.trim() === '') {
    // 如果没有输入姓名，则显示所有学生
    students.value = allStudents.value;
  } else {
    // 根据姓名过滤学生
    students.value = allStudents.value.filter(student => 
      student.name.includes(name.value.trim())    //用于检查一个字符串是否包含另一个字符串。//获取输入框中的 name 值，并使用 .trim() 方法去除前后空格。
    );
  }
  // 显示查询结果
showResults.value = true;
}


  </script>
  
  <style scoped>
  /* 简单的样式 */
  h1 {
    text-align: center;
    margin-top: 20px;
  }
  form {
    display: flex;
    justify-content: center;
    margin-top: 20px;
  }
  input {
    padding: 8px;
    margin-right: 10px;
  }
  button {
    padding: 8px 16px;
    background-color: #6ed872;
    color: white;
    border: none;
    cursor: pointer;
  }
  button:hover {
    background-color: #5bcf61;
  }
  table {
    margin: 20px auto;
    width: 80%;
    border-collapse: collapse;
  }
  th, td {
    padding: 10px;
    text-align: center;
    border: 1px solid #ddd;
  }
  </style>
  