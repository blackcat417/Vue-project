<template>
  <ul class="list">
    <li
      class="list__item"
      v-for="todoItem in todoItems"
      v-bind:key="todoItem.item"
    >
      <input
        type="checkbox"
        v-bind:id="todoItem.item"
        v-bind:checked="todoItem.completed === true"
        v-on:change="toggleComplete(todoItem)"
      />
      <label v-bind:for="todoItem.item" class="list__label">
        <p class="list__text">{{ todoItem.item }}</p>
      </label>
      <p class="list__date">{{ todoItem.date }}</p>
    </li>
  </ul>
</template>

<script>
export default {
  data() {
    return {
      todoItems: [],
    };
  },
  created() {
    if (localStorage.length > 0) {
      for (let i = 0; i < localStorage.length; i++) {
        if (localStorage.key(i) !== "loglevel:webpack-dev-server") {
          this.todoItems.push(
            JSON.parse(localStorage.getItem(localStorage.key(i)))
          );
        }
      }
    }
  },
  methods: {
    toggleComplete(todoItem) {
      todoItem.completed = !todoItem.completed;
      localStorage.setItem(todoItem.item, JSON.stringify(todoItem));
    },
  },
};
</script>

<style scoped>
.list {
  display: grid;
  justify-content: center;
  align-items: center;
  background-color: rgb(211, 225, 255);
  padding: 10px;
  border-radius: 3px;
  list-style: none;
}

.list__item {
  display: flex;
  align-items: center;
  justify-content: start;
  background-color: white;
  padding: 10px;
  border-radius: 8px;
  margin-bottom: 10px;

  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

.list__checkbox {
  margin-right: 10px;
  width: 20px;
  height: 20px;
  cursor: pointer;
}
.list__checkbox:checked + .list__label .list__text {
  text-decoration: line-through;
  color: lightgray;
}

.list__text {
  flex-grow: 1;
  margin-left: 10px;
  font-size: 18px;
  font-weight: 600;
}

.list__label {
  display: flex;
  align-items: center;
}

.list__date {
  margin: 0 10px;
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
  background-color: #ff7979;
}
</style>
