<template>
  <input
    type="text"
    class="todoinput"
    @keydown.enter="addNewTodo"
    v-model="content"
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

<style lang="scss"></style>
