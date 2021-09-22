<template>
  <div id="counter">
    <button @click="count++">Add 1</button>
    <button @click="subtract">Subtract 1</button>
    <p>The number is {{ count }}</p>
  </div>
</template>

<script>
export default {
  name: "Counter",
  data() {
    return {
      count: 0,
    };
  },
  methods: {
    subtract: function() {
      if (this.count > 0) {
        this.count--;
      } else {
        alert("count cannot be negative");
      }
    },
  },
};
</script>