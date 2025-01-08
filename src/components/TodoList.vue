<template>
  <ul class="list">
    <input type="checkbox" id="list-item-1" />
    <label for="list-item-1">
      <p class="list__text">Smile! :)</p>
    </label>
    <p class="list__date">5/26</p>
    <button class="list__delete">Delete</button>
  </ul>
</template>

<style scoped>
.list {
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: #f0f8ff;
  padding: 10px;
  border-radius: 8px;
  margin: 20px 0;
  list-style: none;
}

.list__item {
  display: flex;
  align-items: center;
  justify-content: space-between;
  background-color: white;
  padding: 15px;
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
  margin: 0;
  font-size: 18px;
  font-weight: 600;
}

.list__label {
  display: flex;
  align-items: center;
}

.list__date {
  margin: 0 10px;
  font-size: 14px;
  color: gray;
}

.list__delete {
  background-color: #ff5252;
  color: white;
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
