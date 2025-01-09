<template>
  <ul class="list">
    <li
      class="list__item"
      v-for="(todoItem, index) in propsdata"
      v-bind:key="todoItem.item"
    >
      <div class="list__left">
        <input
          type="checkbox"
          v-bind:id="todoItem.item"
          v-bind:checked="todoItem.completed === true"
          v-on:change="toggleComplete(todoItem)"
          class="list__checkbox"
        />
        <label v-bind:for="todoItem.item" class="list__label">
          <p class="list__text">{{ todoItem.item }}</p>
        </label>
      </div>
      <div class="list__right">
        <p class="list__date">{{ todoItem.date }}</p>
        <button class="list__delete" v-on:click="removeTodo(todoItem, index)">
          <div class="blind">Delete</div>
        </button>
      </div>
    </li>
  </ul>
</template>

<script>
export default {
  props: ["propsdata"],

  methods: {
    toggleComplete(todoItem) {
      this.$emit("toggleItem", todoItem);
    },
    removeTodo(todoItem, index) {
      this.$emit("removeItem", todoItem, index);
    },
  },
};
</script>

<style scoped>
.list {
  display: grid;
  justify-content: center;
  align-items: center;
  background-color: #f0f8ff;
  padding: 10px;
  border-radius: 3px;
  list-style: none;
}

.list__item {
  width: 400px;
  display: flex;
  align-items: center;
  justify-content: space-between;
  background-color: white;
  padding: 10px;
  border-radius: 8px;
  margin-bottom: 10px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

.list__left {
  display: flex;
  align-items: center;
}

.list__checkbox {
  margin-right: 10px;
  width: 20px;
  height: 20px;
  cursor: pointer;
}

.list__label {
  display: flex;
  align-items: center;
}

.list__text {
  flex-grow: 1;
  margin-left: 10px;
  font-size: 18px;
  font-weight: 600;
}

.list__right {
  display: flex;
  align-items: center;
  gap: 10px;
}

.list__date {
  font-size: 15px;
  color: gray;
}

.list__delete {
  background-color: transparent;
  color: grey;
  border: none;
  border-radius: 8px;
  padding: 8px 12px;
  cursor: pointer;
  font-size: 14px;
}

.list__delete:hover {
  cursor: pointer;
  background-color: #ff7979;
}
</style>
