<template>
  <div id="app">
    <p>{{ title }}</p>
    <p>נותרו לך {{totalTodos}} משימות</p>
    <button @click="addTodo">הוסף משימה</button>
    <input type="text" v-model="newTodo" />
    <p>משימות לביצוע</p>
    <table>
      <tr>
        <th>בצע</th>
        <th>תיאור</th>
      </tr>
      <tr v-for="todo in waitingTodos" :key="todo.id">
        <td>
          <button @click="completeTodo(todo.id)">תלחץ אותי</button>
        </td>
        <td>{{ todo.description }}</td>
      </tr>
    </table>
    <p>משימות שבוצעו</p>
    <table>
      <tr>
        <th>בצע</th>
        <th>תיאור</th>
      </tr>
      <tr v-for="todo in completedTodos" :key="todo.id">
        <td>
          <button @click="completeTodo(todo.id)">תלחץ אותי</button>
        </td>
        <td>{{ todo.description }}</td>
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
      newTodo: "",
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
    waitingTodos: function () {
      return this.todos.filter((todo) => !todo.completed);
    },
    completedTodos: function () {
      return this.todos.filter((todo) => todo.completed);
    },
  },
  methods: {
    completeTodo: function (id) {
      const todo = this.todos.find((todo) => todo.id === id);
      todo["completed"] = !todo["completed"];
    },
    addTodo: function () {
      const lastId = this.todos[this.todos.length - 1]["id"];
      const newTodo = {
        id: lastId + 1,
        description: this.newTodo,
        completed: false,
      };
      this.todos.push(newTodo);
    },
  },
  watch: {
    completedTodos: function (newValue, oldValue) {
      if (oldValue.length != 0 && newValue.length == 0) {
        console.log("hi");
        alert("לא ביצעת כלום!");
      }
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
