<template>
  <div>
    <NewTodo @AddTodo="addNewTodo($event)" />
    <div
      :class="[{ done: todoItem.done }, 'incomplete']"
      v-for="(todoItem, i) in Task"
      :key="i"
    >
      <h2>{{ todoItem.content }}</h2>
      <RemoveTodo @removeTodo="removeTodo(i)" />
      <ToggleTodo @toggleTodo="toggleTodo(i)" />
    </div>
  </div>
</template>

<script lang="ts">
import { Options, Vue } from "vue-class-component";
import NewTodo from "./NewTodo.vue";
import RemoveTodo from "./RemoveTodo.vue";
import ToggleTodo from "./ToggleTodo.vue";
import { Task } from "../Models/task";

@Options({
  components: {
    NewTodo,
    RemoveTodo,
    ToggleTodo,
  },
})
export default class Todo extends Vue {
  Task: Task[] = [];

  addNewTodo(t: Task) {
    this.Task.push(t);
  }
  removeTodo(i: number) {
    this.Task.splice(i, 1);
  }
  toggleTodo(i: number) {
    this.Task[i].done = !this.Task[i].done;
    console.log(this.Task[i].done);
  }
}
</script>

<style lang="scss">
.done {
  background: green;
}
</style>
