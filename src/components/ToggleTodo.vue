<template>
  <button
    @click="
      () => {
        toggleTodo(i);
      }
    "
  >
    Toggle done
  </button>
</template>

<script lang="ts">
import { Options, Vue } from "vue-class-component";
import { Task } from "../Models/task";
import { Prop } from "vue-property-decorator";

export default class ToggleTodo extends Vue {
  @Prop() Task!: Task[];

  toggleTodo(i: number) {
    this.$emit("toggleTodo", i);
  }
}
</script>

<style lang="scss"></style>
