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
  background: transparent;
}

.add__input {
  width: 70%;
  padding: 15px;
  border: none;
  border-radius: 25px;
  font-size: 16px;
  outline: none;
  transition: all 0.3s ease;
  box-shadow: 0 2px 10px rgba(88, 88, 88, 0.805);
  background-color: rgba(255, 255, 255, 0.441);
}
.add__input::placeholder {
  color: rgba(
    255,
    255,
    255,
    0.829
  ); /* placeholder 텍스트 색상을 하얀색으로 설정 */
  opacity: 1; /* 기본값은 0.5로 설정되기 때문에, 1로 변경하여 불투명하게 */
}

.add__input:focus {
  border-color: #4facfe;
  box-shadow: 0 0 5px rgba(79, 172, 254, 0.5);
}

.add__button {
  padding: 15px 20px;
  background-color: #9f9f9f;
  color: grey;
  font-size: 16px;
  border: none;
  border-radius: 25px;
  cursor: pointer;

  background-color: rgba(255, 255, 255, 0.692);
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.5);
}

.add__button:hover {
  background-color: #45a049;
}
</style>
