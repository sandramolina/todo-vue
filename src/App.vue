<script>
export default {
  name: 'app',
  data() {
    return {
      newToDo: '',
      existingToDo: [
        { text: 'Get Groceries', id: 0 },
        { text: 'Walk Dog', id: 1 },
        { text: 'Wash dishes', id: 2 },
      ],
    };
  },
  methods: {
    addToDo() {
      this.existingToDo.push({
        text: this.newToDo,
        id: new Date().valueOf(),
      }),
        (this.newToDo = '');
    },
    deleteToDo(index) {
      this.existingToDo.splice(index, 1);
    },
  },
};
</script>

<template>
  <div id="app">
    <div class="container">
      <h1>My TODO List!</h1>
      <input class="input" v-model="newToDo" />
      <button class="add-button" @click="addToDo()">Add</button>
      <ul class="list-todo">
        <li v-for="(todo, index) in existingToDo" :key="index">
          <span
            >{{ index + 1 }}: {{ todo.text }}
            <button class="delete-btn" @click="deleteToDo(index)">
              🗑
            </button></span
          >
        </li>
      </ul>
    </div>
  </div>
</template>

<style>
.list-todo {
  list-style: none;
}
.delete-btn {
  background: none;
  border: none;
  cursor: pointer;
}
</style>
