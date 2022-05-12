<template>
  <input
    type="text"
    class="todoinput"
    @keydown.enter="addNewTodo"
    v-model="content"
    placeholder="Add a Todo"
  />
</template>

<script lang="ts">
import { Options, Vue } from "vue-class-component";
import { Task } from "../Models/task";

export default class NewTodo extends Vue {
  content = "";

  addNewTodo() {
    this.$emit("AddTodo", new Task(this.content));
    this.content = "";
  }
}
</script>

<style lang="scss">
input {
  height: 30px;
  width: 180px;
  border-radius: 10px;
  border: none;
  background-color: rgb(219, 219, 219);

  text-align: center;
}
</style>
