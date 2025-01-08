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
      taskTotal: 5,
    };
  },
};
</script>

<style>
.title {
  background-color: aqua;
  max-width: max-content;
  text-align: center;
  margin-inline: 4;
}
</style>
