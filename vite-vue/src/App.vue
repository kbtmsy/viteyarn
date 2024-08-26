<script>
import TodoAdd from "./components/TodoAdd.vue";

export default {
  components: {
    TodoAdd,
  },
  data() {
    return {
      newTodoText: '',
      todos: [
         { isDone: false, text: 'ToDoの文字列'}
      ],
    }
  },
  methods: {
    addTodo() {
      if (!this.newTodoText) return alert('文字を入力してください')
      this.todos.push({
        isDone: false,
        text: this.newTodoText,
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
  <TodoAdd @delete-done="clearDoneTodos" @add-todo="addTodo"/>
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
