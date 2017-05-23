<script>
export default {
  data() {
    return {
      newStudent: {
        firstname: '',
        lastname: '',
        age: '',
      },
    };
  },
  props: ['student'],
  methods: {
    addStudent() {
      this.$emit('add-student', this.newStudent);
    },
  },
};
</script>

<template>
<div>
<input
    v-model="newStudent.lastname"
    placeholder="LASTNAME"
  >
<input
    v-model="newStudent.firstname"
    placeholder="FIRSTNAME"
  >
<input
    v-model="newStudent.age"
    placeholder="AGE"
  >
  <button @click="addStudent"> Ajouter
  </button>
</div>
</template>

<style>
</style>
