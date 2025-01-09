<template>
  <div class="title">
    <p class="title__message">{{ message }}</p>
    <p class="title__task">
      <span class="title__task-top">You've got </span>
      <span class="title__task-count">
        <em class="title__task-left">{{ propsdata.left }}</em>
        <em v-if="propsdata.total" class="title__task-total"
          >&nbsp; / {{ propsdata.total }}</em
        >
      </span>
      <span class="title__task-bottom">tasks today!</span>
      <span class="title__task-info"></span>
    </p>
  </div>
</template>

<script>
export default {
  props: ["propsdata"],
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
.title__task-left {
  font-size: 50px;
  font-weight: 500;
}
.title__task-total {
  font-size: 30px;
  font-weight: 700;
  color: #f9d342; /* 강조 색상 */
  margin-right: 8px;
}
</style>
