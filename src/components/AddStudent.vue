<script>
export default {
  props: ['student'],
  methods: {
    add() {
      this.$emit('add-student');
    },
  },
};
</script>

<template>
<div>
<input
    v-model="lastname"
    v-on:keyup.enter="addStudent"
    placeholder="LASTNAME"
  >
<input
    v-model="firstname"
    v-on:keyup.enter="addStudent"
    placeholder="FIRSTNAME"
  >
<input
    v-model="age"
    v-on:keyup.enter="addStudent"
    placeholder="AGE"
  >
  <button @click="addStudent"> Ajouter
  </button>
</div>
</template>

<style>
</style>
