<template>
  <header class="header">
    <h1 class="logo">My Todo</h1>
    <p class="date">{{ timestamp }}</p>
  </header>
</template>

<script>
import getDate from "./getDate.js";

export default {
  data() {
    return {
      timestamp: "",
    };
  },
  created() {
    this.timestamp = `${getDate().month}/${getDate().date} ${getDate().week}`;
  },
};
</script>

<style scoped>
.logo {
  font-size: 25px;
  font-weight: 500;
}
.header {
  border-radius: 3px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 10px 20px;
  background-color: rgb(235, 235, 255);
  color: black;
  font-weight: 400;
}
</style>
