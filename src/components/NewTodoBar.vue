<template>
  <div class="container">
    <form class="new-todo-form" @submit.prevent="validateTodo">
      <input type="text" placeholder="all details..." v-model="newTodo" />
      <button type="submit">Add</button>
    </form>
  </div>
</template>

<script>
import { eventBus } from "@/main";

export default {
  name: "new-todo-bar",
  data() {
    return {
      newTodo: "",
    };
  },
  methods: {
    validateTodo() {
      if (this.newTodo.trim().length == 0) {
        alert("todo is empty");
      } else {
        eventBus.$emit("newTodoInput", this.newTodo);
        this.newTodo = "";
      }
    },
  },
};
</script>

<style lang="scss" scoped>
$primary-color: #2f80ed;

.new-todo-form {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 56px;

  input {
    margin-right: 25px;
    padding: 20px 12px;
    border-radius: 12px;
    border: 1px solid #bdbdbd;
    width: 100%;
    font-size: 14px;
  }

  button {
    background-color: $primary-color;
    border: none;
    color: white;
    padding: 20px 40px;
    border-radius: 12px;
  }
}
</style>