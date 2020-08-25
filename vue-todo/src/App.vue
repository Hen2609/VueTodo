<template>
  <div id="app">
    <p>{{ title }}</p>
    <p>נותרו לך {{totalTodos}} משימות</p>
    <table>
      <tr>
        <th>תיאור</th>
        <th>בצע</th>
      </tr>
      <tr v-for="todo in todos" :key="todo.id">
        <td>{{ todo.description }}</td>
        <td>
          <button :disabled="todo.completed" @click="completeTodo(todo.id)">תלחץ אותי</button>
        </td>
      </tr>
    </table>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      title: "רמלה אימפריה",
      todos: [
        { id: 1, description: "Ramle", completed: false },
        { id: 2, description: "Capital", completed: false },
        { id: 3, description: "Center", completed: true },
      ],
    };
  },
  computed: {
    totalTodos: function () {
      return this.todos.filter((todo) => !todo.completed).length;
    },
  },
  methods: {
    completeTodo: function (id) {
      const todo = this.todos.find((todo) => todo.id == id);
      todo["completed"] = true;
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
