<script>
import axios from 'axios';
import StudentLine from './StudentLine';
import AddStudent from './AddStudent';

export default {
  components: {
    StudentLine,
    AddStudent,
  },
  data() {
    return {
      students: [],
    };
  },
  methods: {
    getAll() {
      axios.get('http://localhost:3000/students')
      .then((response) => {
        this.students = response.data;
      });
    },
    addStudent() {
      axios.post('http://localhost:3000/students')
      .then((response) => {
        this.students = response.data;
      });
    },
    remove(index) {
      this.students.splice(index, 1);
    },
  },
  mounted() {
    this.getAll();
    this.add();
  },
};
</script>

<template>
  <div>
    <student-line v-for='(student, index) in students' :student="student" v-on:remove="remove(index)"></student-line>
    <addStudent></addStudent>
  </div>
</template>

<style>
</style>
