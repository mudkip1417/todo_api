<template>

  <div>

    <AddTodo @submit="addTodo" />

    <TodoList :todos="todos" />

  </div>

</template>

<script>

  import AddTodo from "@/components/AddTodo";
  import TodoList from "@/components/TodoList";
  import axios from "@/plugins/axios";

  export default {
    components: {
      AddTodo,
      TodoList,
    },
    data() {
      return {
        todos: [],
      };
    },
    methods: {
      async addTodo(title) {
        await axios.post("/v1/todos", { title });
        this.todos.push({
          title
        });
      },
    },
  };

</script>

<style>
</style>
