<template>
  <div id="students-list">
    <input placeholder="Search" v-model="keywords" />
    <StudentCreator />

    <ul id="students-list-container" v-if="!keywords">
      <li v-for="student in students" :key="student.id">
        <StudentCard :student="student" />
      </li>
    </ul>

    <ul id="students-list-container" v-if="keywords">
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
      if (!this.keywords) return null;
      return this.students.filter((s) => this.isInclude(s));
    },
  },
  methods: {
    isInclude(s) {
      const name = s.firstName.toLowerCase() + " " + s.lastName.toLowerCase();
      return name.includes(this.keywords.toLowerCase());
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
