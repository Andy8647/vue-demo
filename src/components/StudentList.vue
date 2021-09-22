<template>
  <div id="students-list">
    <input placeholder="Search" v-model="keywords" />
    <StudentCreator />

    <ul id="students-list-container">
      <li v-for="student in searchRes" :key="student.id">
        <StudentCard :student="student" />
      </li>
    </ul>
  </div>
</template>

<script>
import axios from "axios";
import StudentCard from "./StudentCard.vue";
import StudentCreator from "./StudentCreator.vue";

const url = "https://api.hatchways.io/assessment/students";

export default {
  name: "StudentList",
  components: {
    StudentCard,
    StudentCreator,
  },
  data() {
    return {
      students: null,
      keywords: null,
    };
  },
  computed: {
    searchRes: function() {
      const isInclude = (s) => {
        const name = s.firstName.toLowerCase() + " " + s.lastName.toLowerCase();
        return name.includes(this.keywords.toLowerCase());
      };
      if (!this.keywords) {
        return this.students;
      } else {
        if (!this.students.some(isInclude)) {
          return null;
        } else {
          return this.students.filter((s) => isInclude(s));
        }
      }
    },
  },
  mounted: function() {
    axios
      .get(url)
      .then((res) => {
        this.students = res.data.students;
      })
      .catch((error) => {
        console.log(error);
      });
  },
};
</script>

<style scoped>
#students-list {
  width: 1000px;
  height: 800px;
  overflow: scroll;
  margin-left: auto;
  margin-right: auto;
  box-shadow: 2px 5px 20px 1px grey;
  border-radius: 0.25rem;
}
#students-list-container {
  list-style: none;
  padding: 0px;
}
</style>
