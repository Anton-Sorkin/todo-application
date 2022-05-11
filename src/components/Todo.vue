<template>
  <div class="todo-container">
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
import { warn } from "@vue/runtime-core";

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
    if (t.content.length > 0) {
      if (t.content.length < 30) {
        this.Task.push(t);
      } else {
        alert("That's just to much information");
      }
    } else {
      alert("Add atleast one character please");
    }
  }
  removeTodo(i: number) {
    this.Task.splice(i, 1);
  }
  toggleTodo(i: number) {
    this.Task[i].done = !this.Task[i].done;
  }
}
</script>

<style lang="scss">
* {
  margin: 0px;
  padding: 0px;
  box-sizing: border-box;
}
.todo-container {
  background-color: aquamarine;
  height: 100%;
  width: 100vw;

  .incomplete {
    background-color: brown;
  }
  .done {
    background: green;
  }
}
@media (max-width: 640px) {
  .todo-container {
    background-color: rgb(189, 127, 255);
  }
}
@media (min-width: 786px) {
  .todo-container {
    background-color: rgb(255, 127, 127);
  }
}
</style>
