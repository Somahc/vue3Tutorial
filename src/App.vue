<script>
export default {
  data() {
    return {
      taskStatus: {
        isDone: false,
      },
      tasks: [
        {
          taskName: 'Vueをマスターする',
          isDone: true,
        },
        {
          taskName: '牛乳を買う',
          isDone: false,
        },
        {
          taskName: '家賃を払う',
          isDone: false,
        },
      ],
      input: {
        taskName: '',
        isDone: false,
      },
    }
  },
  methods: {
    addTask() {
      if (!this.input.taskName) {
        alert('タスク名を入力してください')
        return
      }
      this.tasks.push(this.input)
      this.input = {
        taskName: '',
        isDone: false,
      }
    },
    removeTask() {
      this.tasks = this.tasks.filter((task) => !task.isDone)
    },
  },
  computed: {},
}
</script>

<template>
  <h1>My ToDo App</h1>
  <input type="text" v-model="input.taskName" /><button @click="addTask">
    追加</button
  ><button @click="removeTask">完了済みを削除する</button>
  <div v-if="tasks.length === 0">タスクがありません</div>
  <div v-else>
    <ul>
      <li v-for="task in tasks">
        <input type="checkbox" v-model="task.isDone" /><span
          v-bind:class="{ 'todo-done': task.isDone }"
          >{{ task.taskName }}</span
        >
      </li>
    </ul>
  </div>
</template>

<style>
body {
  background-color: #eee;
}

.todo-done {
  text-decoration: line-through;
}
</style>
