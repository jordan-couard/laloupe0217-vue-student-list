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
      axios.get('/api/students')
      .then((response) => {
        this.students = response.results;
      });
    },
    addStudent(student) {
      axios.post('/api/students/', student)
      .then(() => {
        this.getAll();
      });
    },
    remove(index) {
      axios.delete(`/api/students/${this.students[index].id}`)
      .then(() => {
        this.getAll();
      });
    },
  },
  mounted() {
    this.getAll();
  },
};
</script>

<template>
  <div>
    <StudentLine v-for='(student, index) in students' :student="student" v-on:remove="remove(index)"></StudentLine>
    <addStudent @add-student='addStudent'></addStudent>
  </div>
</template>

<style>
</style>
