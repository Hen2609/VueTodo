<template>
  <tr>
    <td>
      <button @click="changeCompletion(todo.id)">{{buttonText}}</button>
    </td>
    <td>{{ todo.description }}</td>
  </tr>
</template>

<script>
export default {
  props: ["todo"],
  computed: {
    buttonText: function () {
      if (this.todo.completed) {
        return "בטל";
      } else {
        return "בצע";
      }
    },
  },
  methods: {
    changeCompletion: function () {
      this.$emit("completionChanged", this.todo.id);
    },
  },
};
</script>

<style>
</style>