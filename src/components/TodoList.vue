<script>
export default {
  data() {
    return {
      //   todos: [{ isDone: false, text: 'ToDoの文字列' }],
    }
  },
  props: {
    todoss: Array,
  },
}
</script>

<template>
  <ul>
    <li v-for="todo in todoss">
      <input type="checkbox" v-model="todo.isDone" /><span
        :class="{ 'todo-done': todo.isDone }"
        >{{ todo.text }}</span
      >
    </li>
  </ul>
</template>
