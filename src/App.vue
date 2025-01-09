<template>
  <div id="app">
    <div class="main-container">
      <TodoHeader />
      <TodoTitle v-bind:propsdata="checkCount" />
      <TodoInput v-on:addItem="addOneItem" />
    </div>
    <TodoController v-on:clearAll="clearAllItems" />
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
  computed: {
    checkCount() {
      const checkLeftItems = () => {
        let leftCount = 0;
        for (let i = 0; i < this.todoItems.length; i++) {
          if (this.todoItems[i].completed === false) {
            leftCount++;
          }
        }
        return leftCount;
      };
      const count = {
        total: this.todoItems.length,
        left: checkLeftItems(),
      };
      return count;
    },
  },
  methods: {
    sortTodoLatest() {
      this.todoItems.sort(function (a, b) {
        return b.time - a.time;
      });
    },
    sortTodoOldest() {
      this.todoItems.sort(function (a, b) {
        return a.time - b.time;
      });
    },
    sortAllItem(selectedSort) {
      if (selectedSort.value === "date-desc") {
        this.sortTodoLatest();
      } else if (selectedSort.value === "date-asc") {
        this.sortTodoOldest();
      }
    },
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
    clearAllItems() {
      this.todoItems = [];
      localStorage.clear();
    },
  },
  mounted() {
    this.sortTodoOldest();
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
.main-container {
  background: linear-gradient(
    135deg,
    #4facfe,
    #f093fb
  ); /* 파란색에서 핑크색으로 그라데이션 */
  padding: 20px 0;
}
#app {
  background: linear-gradient(135deg, #4facfe, #f093fb);
}
</style>
