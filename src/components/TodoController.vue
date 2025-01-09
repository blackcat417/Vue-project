<template>
  <div class="controller">
    <div class="select">
      <select name="order" id="order" class="selectbox">
        <option value="date-asc">Date Ascending</option>
        <option value="date-desc">Date Descending</option>
        <option value="name-asc">Name Ascending</option>
        <option value="name-desc">Name Descending</option>
      </select>
    </div>
    <button class="clear" v-on:click="clearTodo">Clear All</button>
  </div>
</template>

<script>
export default {
  methods: {
    clearTodo() {
      this.$emit("clearAll");
    },
  },
};
</script>

<style scoped>
.controller {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin: 20px 10px;
}

.select {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.select-label {
  font-size: 14px;
  margin-bottom: 4px;
}

.selectbox {
  margin-top: 5px;
  padding: 8px 12px;
  font-size: 16px;
  border: 1px solid #ddd;
  border-radius: 8px;
  background-color: white;
  appearance: none;
  outline: none;
  cursor: pointer;
}

.selectbox:focus {
  border-color: #4facfe;
}

.clear {
  padding: 10px 16px;
  background-color: transparent;
  border: none;
  border-radius: 8px;
  color: grey;
  font-size: 16px;
  text-decoration: underline;
  cursor: pointer;
}

.clear:hover {
  cursor: pointer;
}
</style>
