<template>
  <div class="add">
    <input
      type="text"
      class="add__input"
      placeholder="Enter your task here"
      v-model="newTodoItem"
      v-on:keyup.enter="addTodoItem"
    />
    <button class="add__button" @click="addTodoItem">
      <span class="blind">Add</span>
    </button>
  </div>
</template>

<script>
import getDate from "./getDate.js";

export default {
  data() {
    return {
      newTodoItem: "",
    };
  },
  methods: {
    addTodoItem() {
      if (this.newTodoItem !== "") {
        this.$emit("addItem", this.newTodoItem);
        this.clearInput();
        var value = {
          item: this.newTodoItem,
          date: `${getDate().date} ${getDate().week}`,
          time: getDate().time,
          completed: false,
        };
        localStorage.setItem(this.newTodoItem, JSON.stringify(value));
        this.clearInput();
      }
    },
    clearInput() {
      this.newTodoItem = "";
    },
  },
};
</script>

<style>
.add {
  display: flex;
  justify-content: center;
  align-items: center;
  margin: 10px 0;
  gap: 10px;
}

.add__input {
  width: 70%;
  padding: 15px;
  border: 1px solid #ddd;
  border-radius: 25px;
  font-size: 16px;
  outline: none;
  transition: all 0.3s ease;
}

.add__input:focus {
  border-color: #4facfe;
  box-shadow: 0 0 5px rgba(79, 172, 254, 0.5);
}

.add__button {
  padding: 15px 20px;
  background-color: #9f9f9f;
  color: white;
  font-size: 16px;
  border: none;
  border-radius: 25px;
  cursor: pointer;
  transition: background-color 0.3s ease;
}

.add__button:hover {
  background-color: #45a049;
}
</style>
