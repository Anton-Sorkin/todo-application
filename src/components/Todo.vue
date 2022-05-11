<template>
  <div>
    <NewTodo @AddTodo="addNewTodo($event)" />
    <div v-for="(todoItem, i) in Task" :key="i">
      <div>
        <h2>{{ todoItem.content }}</h2>
        <RemoveTodo @removeTodo="removeTodo(i)" />
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { Options, Vue } from "vue-class-component";
import NewTodo from "./NewTodo.vue";
import RemoveTodo from "./RemoveTodo.vue";
import { Task } from "../Models/task";

@Options({
  components: {
    NewTodo,
    RemoveTodo,
  },
})
export default class Todo extends Vue {
  isActive = false;
  Task: Task[] = [];

  addNewTodo(t: Task) {
    this.Task.push(t);
  }
  removeTodo(i: number) {
    this.Task.splice(i, 1);
  }
}
</script>

<style lang="scss"></style>
