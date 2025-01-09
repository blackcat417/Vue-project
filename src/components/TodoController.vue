<template>
  <div class="controller">
    <div class="select">
      <select
        name="order"
        id="order"
        class="selectbox"
        v-model="selected"
        v-on:change="sortTodo"
      >
        <option value="date-asc">오래된순</option>
        <option value="date-desc">최신순</option>
      </select>
    </div>
    <button class="clear" v-on:click="clearTodo">Clear All</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      selected: "date-asc",
    };
  },
  methods: {
    clearTodo() {
      this.$emit("clearAll");
    },
    sortTodo() {
      this.$emit("sortItem", { value: this.selected });
    },
  },
};
</script>

<style scoped>
.controller {
  background-color: #e6e6e6;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding-top: 10px;
}

.select {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.select-label {
  font-size: 12px;
  margin-bottom: 4px;
}

.selectbox {
  padding: 8px 12px;
  margin-left: 10px;
  font-size: 14px;
  border: 1px solid #ddd;
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
