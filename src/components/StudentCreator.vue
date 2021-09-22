<template>
  <div>
    <input placeholder="First Name" v-model="firstName" />
    <input placeholder="Last Name" v-model="lastName" />
    <input placeholder="City" v-model="city" />
  </div>
</template>

<script>
export default {
  name: "StudentCreator",
  data() {
    return {
      firstName: null,
      lastName: null,
      city: null,
      grades: null,
    };
  },
  mounted: function() {
    this.grades = Array.from({ length: 8 }, () =>
      Math.floor(Math.random() * 100)
    );
  },
};
</script>
