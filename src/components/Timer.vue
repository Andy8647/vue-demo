<template>
  <div id="timer">
    <p>Time: {{ localTime }}</p>
  </div>
</template>

<script>
export default {
  name: "Timer",
  data() {
    return {
      time: new Date(),
    };
  },
  computed: {
    localTime: function() {
      return this.time.toLocaleString();
    },
  },
  beforeCreate: function() {
    console.log("timer before created at", this.localTime);
  },
  created: function() {
    console.log("timer createrd at ", this.localTime);
  },
  beforeMount: function() {
    console.log("timer before mounted at ", this.$el);
  },
  mounted: function() {
    console.log("timer mounted at ", this.$el);

    let _this = this;
    this.timer = setInterval(() => {
      _this.time = new Date();
    }, 1000);
  },
  beforeUpdate: function() {
    // console.log("timer before upodate ", this.time);
  },
  updated: function() {
    // console.log("timer updated ", this.$data);
  },
  beforeDestroy: function() {
    console.log("timer to be destroyed", this.$el);

    if (this.tiemr) {
      clearInterval(this.timer);
    }
  },
  destroyed: function() {
    console.log("timer destoryed", this.$el);
  },
};
</script>

<style scoped>
p {
  font-size: 25px;
  font-weight: 900;
}
</style>
