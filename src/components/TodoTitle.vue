<template>
  <div class="title">
    <p class="title__message">{{ message }}</p>
    <p class="title__task">
      You've got<span class="title__task-total">{{ taskTotal }}</span> tasks
      today.
    </p>
  </div>
</template>

<script>
export default {
  data() {
    return {
      message: "Hello, soo.",
      taskTotal: 10,
    };
  },
};
</script>

<style>
.title {
  color: black;
  text-align: center;
  margin-top: 40px;
  font-family: "Jost", sans-serif;
}
.title__message {
  font-size: 25px;
  margin-bottom: 8px;
  font-weight: 300;
}

.title__task {
  font-size: 24px;
  font-weight: 500;
}

.title__task-total {
  font-size: 48px;
  font-weight: 700;
  color: #f9d342; /* 강조 색상 */
  margin-left: 8px;
}
</style>
