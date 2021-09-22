<template>
  <div class="student-card-area">
    <img :src="student.pic" alt="" />
    <span>{{ name }}</span>
    <br />
    <span v-bind:title="student.grades">Average Score: {{ avgScore }}</span>
  </div>
</template>

<script>
export default {
  name: "StudentCard",
  props: ["student"],
  computed: {
    name: function() {
      return this.student.firstName + " " + this.student.lastName;
    },
    avgScore: function() {
      const grades = this.student.grades.map((g) => {
        return parseInt(g);
      });
      return (
        grades.reduce((sum, value) => {
          return sum + value;
        }, 0) / grades.length
      );
    },
  },
};
</script>

<style scoped>
.student-card-area {
  margin: 10px;
  border: 1px solid black;
}
</style>
