<template>
  <div class="add">
    <input type="text" class="add__input" placeholder="Enter your task" />
    <button class="add__button">➜</button>
  </div>
</template>

<style>
.add {
  .add {
    display: flex;
    justify-content: center;
    align-items: center;
    margin: 20px 0;
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
    background-color: #4caf50;
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
}
</style>
