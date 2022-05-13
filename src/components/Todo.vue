<template>
  <div class="todo-container">
    <NewTodo @AddTodo="addNewTodo($event)" />
    <div
      :class="[{ done: todoItem.done }, 'incomplete']"
      v-for="(todoItem, i) in Task"
      :key="i"
    >
      <div class="text-area">
        <h2>{{ todoItem.content }}</h2>
      </div>
      <div class="todo-btns">
        <RemoveTodo @removeTodo="removeTodo(i)" />
        <ToggleTodo @toggleTodo="toggleTodo(i)" />
      </div>
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
  height: 100%;
  width: 100vw;
  .incomplete {
    background-color: rgb(222, 222, 222);
    height: 100px;
    width: 100%;
    margin-top: 20px;
    display: flex;
    justify-content: space-around;
    align-items: center;
    .text-area {
      width: 60vw;
    }
    .todo-btns {
      height: 35px;
      width: 200px;
      display: flex;
      justify-content: space-around;
      align-items: center;
      button {
        border: none;
        height: 27.5px;
        width: 85px;
        border-radius: 10px;
        background-color: rgb(184, 184, 184);
      }
    }
  }
  .done {
    background: rgb(119, 119, 119);
  }
}
@media (max-width: 640px) {
  .todo-container {
    .incomplete {
      display: flex;
      flex-direction: column;
      .text-area {
        h2 {
          font-size: 12pt;
        }
      }
    }
  }
}
@media (min-width: 876px) {
  .todo-container {
    .incomplete {
      margin-top: 40px;
      .text-area {
        h2 {
          font-size: 20pt;
        }
      }
    }
  }
}
</style>
