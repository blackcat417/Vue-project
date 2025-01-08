<template>
  <div class="controller">
    <div class="select">
      <label for="order">Order</label>
      <select name="order" id="order" class="selectbox">
        <option value="date-asc">Date Ascending</option>
        <option value="date-desc">Date Descending</option>
        <option value="name-asc">Name Ascending</option>
        <option value="name-desc">Name Descending</option>
      </select>
    </div>
    <button class="clear">Clear All</button>
  </div>
</template>

<style scoped>
.controller {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin: 20px 0;
}

.select {
  display: flex;
  flex-direction: column;
}

.select-label {
  font-size: 14px;
  margin-bottom: 4px;
}

.selectbox {
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
  background-color: #ff5252;
  border: none;
  border-radius: 8px;
  color: white;
  font-size: 16px;
  cursor: pointer;
}

.clear:hover {
  background-color: #ff7979;
}
</style>
