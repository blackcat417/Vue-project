<template>
  <div id="app">
    <TodoHeader />
    <TodoTitle />
    <TodoInput v-on:addItem="addOneItem" />
    <TodoController />
    <TodoList
      v-bind:propsdata="todoItems"
      v-on:removeItem="removeOneItem"
      v-on:toggleItem="toggleOneItem"
    />
    <TodoFooter />
  </div>
</template>

<script>
import TodoController from "./components/TodoController.vue";
import TodoFooter from "./components/TodoFooter.vue";
import TodoHeader from "./components/TodoHeader.vue";
import TodoInput from "./components/TodoInput.vue";
import TodoList from "./components/TodoList.vue";
import TodoTitle from "./components/TodoTitle.vue";
import getDate from "./components/getDate";

export default {
  data() {
    return {
      todoItems: [],
    };
  },
  methods: {
    clearAllItem() {
      this.todoItems = [];
      localStorage.clear();
    },
    removeOneItem(todoItem, index) {
      localStorage.removeItem(todoItem.item);
      this.todoItems.splice(index, 1);
    },
    toggleOneItem(todoItem) {
      todoItem.completed = !todoItem.completed;
      localStorage.setItem(todoItem.item, JSON.stringify(todoItem));
    },
    addOneItem(todoItem) {
      var value = {
        item: todoItem,
        date: `${getDate().month}/${getDate().date} ${getDate().week}`,
        time: getDate().time,
        completed: false,
      };
      localStorage.setItem(todoItem, JSON.stringify(value));
      this.todoItems.push(value);
    },
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
  components: {
    TodoHeader,
    TodoTitle,
    TodoInput,
    TodoController,
    TodoList,
    TodoFooter,
  },
};
</script>

<style>
.app {
  background-color: black;
}
</style>
