<template>
  <div id="app">
    <p>Awesome Todo App</p>
    <table>
      <tr>
        <th>תיאור</th>
        <th>בצע</th>
      </tr>
      <tr v-for="(todo,index) in todos" :key="index">
        <td>{{todo}}</td>
        <td>
          <button>תלחץ אותי</button>
        </td>
      </tr>
    </table>
  </div>
</template>

<script>
export default {
  name: "App",
  methods: {},
  data() {
    return {
      todos: ["daniel", "sabag", "wasHere"],
    };
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
