<template>
  <div>
    <p>{{title}}</p>
    <table>
      <tr>
        <th>בצע</th>
        <th>תיאור</th>
      </tr>
      <todoTask
        v-for="todo in todos"
        :key="todo.id"
        :todo="todo"
        @completionChanged="todoCompletionChanged"
      />
    </table>
  </div>
</template>

<script>
import todoTask from "./todoTask.vue";
export default {
  components: {
    todoTask,
  },
  props: ["todos", "title", "tableEmptiedAlert"],
  methods: {
    todoCompletionChanged: function (todoId) {
      this.$emit("todoCompletionChanged", todoId);
    },
  },
  watch: {
    todos: function (newValue, oldValue) {
      if (
        this.tableEmptiedAlert != undefined &&
        oldValue.length != 0 &&
        newValue.length == 0
      ) {
        alert(this.tableEmptiedAlert);
      }
    },
  },
};
</script>