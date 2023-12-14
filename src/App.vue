<script>
import ToDoAdd from './components/ToDoAdd.vue'

export default {
  components: {
    ToDoAdd,
  },
  data() {
    return {
      todos: [{ isDone: false, text: 'ToDoの文字列' }],
    }
  },
  methods: {
    addTodo(newTodoText) {
      if (!newTodoText) return alert('文字を入力してください')
      this.todos.push({
        isDone: false,
        text: newTodoText,
      })
      this.newTodoText = ''
    },
    clearDoneTodos() {
      this.todos = this.todos.filter((todo) => !todo.isDone)
    },
  },
}
</script>

<template>
  <h1>My ToDo App</h1>
  <ToDoAdd @delete-done="clearDoneTodos" @add-todo="addTodo" />
  <!-- <input type="text" v-model="newTodoText" /><button @click="addTodo">
    追加</button
  ><button @click="clearDoneTodos">完了済みを削除する</button> -->
  <p v-if="todos.length === 0">ToDoがまだありません！</p>
  <ul v-else>
    <li v-for="todo in todos">
      <input type="checkbox" v-model="todo.isDone" /><span
        :class="{ 'todo-done': todo.isDone }"
        >{{ todo.text }}</span
      >
    </li>
  </ul>
</template>

<style>
body {
  background-color: #eee;
}

.todo-done {
  text-decoration: line-through;
}
</style>
