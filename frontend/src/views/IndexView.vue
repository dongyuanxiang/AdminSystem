<template>
  <div>
    <el-table :data="studentList" border style="width: 100%" stripe ref="multipleTable" tooltip-effect="dark">
      <el-table-column prop="id" label="id"></el-table-column>
      <el-table-column prop="name" label="姓名"></el-table-column>
      <el-table-column prop="student_id" label="学号"></el-table-column>
      <el-table-column prop="bj_name" label="班级"></el-table-column>
      <el-table-column label="修改">
        <template v-slot="scope">
          <el-button type="danger" @click="updateStudent(scope.row.id)">修改</el-button>
        </template>
      </el-table-column>
      <el-table-column label="删除">
        <template v-slot="scope">
          <el-button type="danger" @click="deleteStudent(scope.row.id)">删除</el-button>
        </template>
      </el-table-column>
    </el-table>
  </div>

</template>

<script>

import axios from "axios";

export default {
  name: "IndexView",
  data(){
    return{
      studentList:axios.get("/studentList").then((data) =>{
        this.studentList = data.data
      })
    }
  }
}

</script>

<script setup>
const addStudent = () =>{

}
const deleteStudent = (id) =>{
  alert(id);
  axios.post("deleteStudent",{
    id: id
  },{
    headers:{
      'Content-Type': 'application/x-www-form-urlencoded'
    },
    withCredentials:true
  })
}
const updateStudent = (id) => {
  alert(id)
}
const commit = (id,name,student_id,bj_name) => {
  alert(id,name,student_id,bj_name)
}
</script>

<style scoped>

</style>